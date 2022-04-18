# MongoDB

1.导入依赖

```
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>
```



2.配置

```yaml
spring:
  data:
    mongodb:
      uri: mongodb://localhost:27017/demo
```



3.使用

dao:

```java
public interface BlockRepository extends MongoRepository<BlockEntity,String> {
}
```

entity:

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
@Document("block")
public class BlockEntity implements Serializable {

    @Field
    private String name;

    @Field
    private String content;
}
```

