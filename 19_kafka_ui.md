# Kafka UI

https://docs.kafka-ui.provectus.io

https://hub.docker.com/r/provectuslabs/kafka-ui

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: kafka-ui-ssl
  namespace: app
binaryData:
  truststore.jks: ___
```

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: kafka-ui-yaml
  namespace: app
data:
 config.yaml: |
    dynamic:
      config:
        enabled: true
        path: /etc/kafka-ui-dynamic-config/dynamic_config.yaml

    server:
      port: 8080
      servlet:
        contextPath: /kafka-ui
    
    auth:
      type: 'LOGIN_FORM'

    spring:
      security:
        user.name: '___'
        user.password: '___'

    kafka:
      clusters:
        - name: glo-non-prod
          bootstrapServers: host1:9092,host2:9092,host3:9092
          properties:
            security.protocol: SASL_SSL
            sasl.mechanism: SCRAM-SHA-512
            sasl.jaas.config: org.apache.kafka.common.security.scram.ScramLoginModule required username="___" password="___";
            ssl:
              truststore:
                location: /ssl/truststore.jks
                password: '___'
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: kafka-ui
  namespace: app
  labels:
    app: kafka-ui
spec:
  serviceAccountName: default
  containers:
    - name: kafka-ui
      image: provectuslabs/kafka-ui:latest
      env:
        - name: TZ
          value: "Asia/Bangkok"
        - name: SPRING_CONFIG_ADDITIONAL-LOCATION
          value: "/etc/kafka-ui-static-config/config.yaml"
      ports:
        - containerPort: 8080
      volumeMounts:
        - name: kafka-ui-yaml
          mountPath: /etc/kafka-ui-static-config
        - name: kafka-ui-dynamic-config
          mountPath: /etc/kafka-ui-dynamic-config
        - name: kafka-ui-ssl
          mountPath: /ssl
      resources:
        requests:
          memory: 256Mi
          cpu: "200m"
        limits:
          memory: 512Mi
          cpu: "500m"
      readinessProbe:
        httpGet:
          path: /kafka-ui/actuator/health
          port: 8080
        initialDelaySeconds: 5
        periodSeconds: 5
        timeoutSeconds: 2
      livenessProbe:
        httpGet:
          path: /kafka-ui/actuator/health
          port: 8080
        initialDelaySeconds: 15
        periodSeconds: 15
        timeoutSeconds: 2
  restartPolicy: Always

  volumes:
    - name: kafka-ui-yaml
      configMap:
        name: kafka-ui-yaml
    - name: kafka-ui-ssl
      configMap:
        name: kafka-ui-ssl
    - name: kafka-ui-dynamic-config
      emptyDir:
        sizeLimit: "100Mi"
```

```yaml
apiVersion: v1
kind: Service
metadata:
  name: kafka-ui-service
  namespace: app
  labels:
    app: kafka-ui
spec:
  type: NodePort
  selector:
    app: kafka-ui
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8080
```
