# Swagger



依赖

```
<dependency>
  <groupId>io.springfox</groupId>
  <artifactId>springfox-boot-starter</artifactId>
  <version>3.0.0</version>
</dependency>
<dependency>
  <groupId>io.springfox</groupId>
  <artifactId>springfox-oas</artifactId>
  <version>3.0.0</version>
</dependency>
```





配置

```
@Configuration
@EnableOpenApi
public class SwaggerConfig {

    @Bean
    Docket docket() {
        return new Docket(DocumentationType.OAS_30)
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.alants.jiandown.controller"))
                .build();
    }
}
```

