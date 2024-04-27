# kafka
```
openssl req -new -x509 -keyout ca-key.pem -out ca-cert.pem -days 3650
keytool -keystore kafka.zookeeper.truststore.jks -alias ca-cert -import -file ca-cert.pem
keytool -keystore kafka.zookeeper.keystore.jks -alias zookeeper -validity 3650 -genkeypair -keyalg RSA -ext SAN=dns:localhost
keytool -keystore kafka.zookeeper.keystore.jks -alias zookeeper -certreq -file ca-request-zookeeper.csr

openssl x509 -req -CA ca-cert.pem -CAkey ca-key.pem -in ca-request-zookeeper.csr -out ca-signed-zookeeper.pem -days 3650 -CAcreateserial

keytool -keystore kafka.zookeeper.keystore.jks -alias ca-cert -import -file ca-cert.pem
keytool -keystore kafka.zookeeper.keystore.jks -alias zookeeper -import -file ca-signed-zookeeper.pem




keytool -keystore kafka.zookeeper-client.truststore.jks -alias ca-cert -import -file ca-cert.pem

keytool -keystore kafka.zookeeper-client.keystore.jks -alias zookeeper-client -validity 3650 -genkeypair -keyalg RSA -ext SAN=dns:localhost

keytool -keystore kafka.zookeeper-client.keystore.jks -alias zookeeper-client -certreq -file ca-request-zookeeper-client.csr

openssl x509 -req -CA ca-cert.pem -CAkey ca-key.pem -in ca-request-zookeeper-client.csr -out ca-signed-zookeeper-client.pem -days 3650 -CAcreateserial

keytool -keystore kafka.zookeeper-client.keystore.jks -alias ca-cert -import -file ca-cert.pem


keytool -keystore kafka.zookeeper-client.keystore.jks -alias zookeeper-client -import -file ca-signed-zookeeper-client.pem


keytool -keystore kafka.broker3.truststore.jks -alias ca-cert -import -file ca-cert.pem
keytool -keystore kafka.broker3.keystore.jks -alias broker3 -validity 3650 -genkeypair -keyalg RSA -ext SAN=dns:localhost

keytool -keystore kafka.broker3.keystore.jks -alias broker3 -certreq -file ca-request-broker3.csr
openssl x509 -req -CA ca-cert.pem -CAkey ca-key.pem -in ca-request-broker3.csr -out ca-signed-broker3.pem -days 3650 -CAcreateserial
keytool -keystore kafka.broker3.keystore.jks -alias ca-cert -import -file ca-cert.pem
keytool -keystore kafka.broker3.keystore.jks -alias broker3 -import -file ca-signed-broker3.pem































keytool -keystore kafka.consumer.truststore.jks -alias ca-cert -import -file ca-cert.pem

keytool -keystore kafka.consumer.keystore.jks -alias consumer -validity 3650 -genkeypair -keyalg RSA -ext SAN=dns:localhost


keytool -keystore kafka.consumer.keystore.jks -alias consumer -certreq -file ca-request-consumer

openssl x509 -req -CA ca-cert.pem -CAkey ca-key.pem -in ca-request-consumer -out ca-signed-consumer -days 3650 -CAcreateserial

keytool -keystore kafka.consumer.keystore.jks -alias ca-cert -import -file ca-cert.pem

keytool -keystore kafka.consumer.keystore.jks -alias consumer -import -file ca-signed-consumer


```
