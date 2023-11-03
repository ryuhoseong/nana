### private method test
#### Reflection
```
Sample sample = new Sample;
Class clazz = Class.forName([full path]);
Method method = clazz.getDeclaredMethod("[method명]", [Parameter Type].class);
method.setAccessible(true);

method.invoke(sample, [parameter]);
```

#### ReflectionTestUtils
```
class A  {
	private method b(String[ ] c){
		---
	}
}

A a =  new A();
ReflectionTestUtils.invokeMethod(a, b, new Object[]{c});
```

### satatic method test
#### build.gradl
```
testImplementation 'org.mockito:mockito-core:4.3.1'
testImplementation 'org.mockito:mockito-inline:4.3.1'
```

#### test code
```
    private static MockedStatic<Runtime> runtimeMockedStatic;

    @BeforeAll
    static void beforeClass() {
        runtimeMockedStatic = mockStatic(Runtime.class);
    }

    @AfterAll
    static void afterClass() {
        runtimeMockedStatic.close();
    }

	@Test
	void java_runtime() {

		Runtime runtimeMock = mock(Runtime.class);
        Process processMock = mock(Process.class);

		String cmd = "ps -ef";

		InputStream targetStream = new ByteArrayInputStream(cmd.getBytes());

        when(Runtime.getRuntime()).thenReturn(runtimeMock);
        when(runtimeMock.exec(any(String.class))).thenReturn(processMock);
        when(processMock.getInputStream()).thenReturn(targetStream);
	}
```

### mock private method inside call method
#### build.gradl

```
Class A {
    private T b;

    private method c(){
        this.b
    }

    public method d(){
        this.c
    }
}

B b = mock(B.class);

A a = new A();
Field field = ReflectionUtils
    .findFields(A.class, f -> f.getName().equals("b"),
    ReflectionUtils.HierarchyTraversalMode.TOP_DOWN)
    .get(0);

field.setAccessible(true);
field.set(a, b);

Method method = A.class.getDeclaredMethod("c");
method.setAccessible(true);

when(method.invoke(a)).thenReturn("");

a.d();
```

### exception test
```
assertThrows(IllegalArgumentException.class
                , () -> {
                    [test 대상 method 호출]
                });
```