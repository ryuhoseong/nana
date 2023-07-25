### filter 추가하는 방법
#### FilterRegistrationBean
```
import org.springframework.boot.web.servlet.FilterRegistrationBean;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import java.util.HashMap;
import java.util.Map;

@Configuration
public class FilterConfig {

    @Bean
    public FilterRegistrationBean<[filter class]> setSessionFilter() {

        FilterRegistrationBean<[filter class]> registrationBean = new FilterRegistrationBean<>();

        registrationBean.setFilter(new [filter class]);
        registrationBean.addUrlPatterns([대상 url]);

        //parameter 전달 필요시
        Map<String, String> initParameter = new HashMap<>();
        registrationBean.setInitParameters(initParameter);

        return registrationBean;

    }

}
```
#### webfilter annotaion
```
@WebFilter(urlPatterns = [url])
public class FilterConfig implements Filter {	
}
```