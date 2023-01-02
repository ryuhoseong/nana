## DataSource
`@DataJpaTest`, `@DataJpaTest` 테스트 진행시 annotation 에 정의된 @AutoConfigureTestDatabase 에 의해
datasource 가 사용자가 properties 에 정의한 datasource 가 아닌 EmbeddedDataSource 로 변경된다.

## 사용자가 properties 에 정의한 datasource 로 변경을 원할시
```
@JdbcTest or @DataJpaTest
@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)
public class Test {
}
```