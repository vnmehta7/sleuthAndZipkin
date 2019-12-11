# Setup Guide

- Zipkin Setup
    - Docker installation of Zipkin service
    ```cmd
        docker run -d -p 9411:9411 openzipkin/zipkin
    ```
    - Once docker image starts running you can access zipkin service by hitting below url from browser
    ```text
        http://localhost:9411/zipkin/
    ```
- Application Setup
    - There are below 4 Springboot applications and they all can be started by bootstrapping jars
        - zipkin-service-1
        - zipkin-service-2
        - zipkin-service-3
        - zipkin-service-4
    - Once applications are running hit below url on browser from zipkin-service-1 and observer logs for all above 4 services. Here you would notice the traceid is same. In these log sample it is **3216daabf2bebca8**
        - Logs from zipkin-service-1
        ```text
              2019-12-11 17:39:30.814  INFO [zipkin-server1,3216daabf2bebca8,3216daabf2bebca8,true] 5532 --- [nio-8081-exec-4] c.e.zipkinservice1.ZipkinController      : Inside zipkinService 1..
        ```
        - Logs from zipkin-service-2
         ```text
              2019-12-11 17:39:31.523  INFO [zipkin-server2,3216daabf2bebca8,115937b2d166611e,true] 8824 --- [nio-8082-exec-1] c.e.zipkinservice2.ZipkinController      : Inside zipkinService 2..
              2019-12-11 17:39:31.523  INFO [zipkin-server2,3216daabf2bebca8,115937b2d166611e,true] 8824 --- [nio-8082-exec-1] c.e.zipkinservice2.ZipkinController      : Now let's create some intentional delay...
              2019-12-11 17:39:51.523  INFO [zipkin-server2,3216daabf2bebca8,115937b2d166611e,true] 8824 --- [nio-8082-exec-1] c.e.zipkinservice2.ZipkinController      : returning afte delay..
         ```
        - Logs from zipkin-service-3
         ```text
              2019-12-11 17:39:52.303  INFO [zipkin-server3,3216daabf2bebca8,7ecd3e90ff743c1f,true] 19288 --- [nio-8083-exec-1] c.e.zipkinservice3.ZipkinController      : Inside zipkinService 3.
         ```
        - Logs from zipkin-service-4
         ```text
              2019-12-11 17:39:52.887  INFO [zipkin-server4,3216daabf2bebca8,695f19a91f3ab153,true] 18388 --- [nio-8084-exec-1] c.e.zipkinservice4.ZipkinController      : Inside zipkinService 4..
         ```
After this you can search with traceid on Zipkin web portal to verify which service took how much time
        
    