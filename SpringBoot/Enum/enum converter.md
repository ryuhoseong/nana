### enum ofLegacyCode 구현
```
@Getter
@AllArgsConstructor
public enum Yn {

    Y("0", "예")
    ;

    private String legacyCode;
    private String desc;

    public static [enum명] ofLegacyCode(String legacyCode) {
        return Arrays.stream([enum명].values())
            .filter(v -> v.getLegacyCode().equals(legacyCode))
            .findAny()
            .orElseThrow(() -> new IllegalArgumentException(String.format("[%s]가 존재하지 않습니다.", legacyCode)));
    }
}
```

### converter 구현
```
import org.springframework.core.convert.converter.Converter;

public class Converter implements Converter<String, [enum명]> {

    @Override
    public [enum명] convert(String legacyCode) {
        return [enum명].ofLegacyCode(legacyCode);
    }

}
```

### formatter 등록
```
@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void addFormatters(FormatterRegistry registry) {
        registry.addConverter(new Converter());
    }

}
```