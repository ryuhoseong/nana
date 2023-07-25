### Deserialization
#### 방법 1 (출처 https://mkyong.com/java/java-serialization-examples/)
```
byte[] bytes = convertObjectToBytes(person);
Person p = (Person) convertBytesToObject(bytes);

 // Convert object to byte[]
public byte[] convertObjectToBytes(java.lang.Object obj) {
    java.io.ByteArrayOutputStream boas = new java.io.ByteArrayOutputStream();
    try (java.io.ObjectOutputStream ois = new java.io.ObjectOutputStream(boas)) {
        ois.writeObject(obj);
        return boas.toByteArray();
    } catch (IOException ioe) {
        ioe.printStackTrace();
    }
    throw new RuntimeException();
}

// Convert byte[] to object
public java.lang.Object convertBytesToObject(byte[] bytes) {
    java.io.InputStream is = new java.io.ByteArrayInputStream(bytes);
    try (java.io.ObjectInputStream ois = new java.io.ObjectInputStream(is)) {
        return ois.readObject();
    } catch (IOException | ClassNotFoundException ioe) {
        ioe.printStackTrace();
    }
    throw new RuntimeException();
}
```

#### 방법 2
```
import com.fasterxml.jackson.databind.ObjectMapper;

ObjectMapper m = new ObjectMapper();
Map<String,Object> props = m.convertValue([대상 class], Map.class);
```