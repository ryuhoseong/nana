### tls1.1 사용가능 방법
```
1. Edit the JRE_HOME/lib/security/java.security file
(Example: C:\program files\java\lib\security\java.security).

2. Search the file for 'jdk.tls.disabledAlgorithms' and you will find a line
that has the disabled protocols, and you will see that TLSv1 and TLSv1.1 are in the list.

Example:

jdk.tls.disabledAlgorithms=SSLv3, TLSv1, TLSv1.1, RC4, DES, MD5withRSA, \
DH keySize < 1024, EC keySize < 224, 3DES_EDE_CBC, anon, NULL, \
include jdk.disabled.namedCurves

3. Remove one or both of them from the disabled protocols line,
then you can restart QIE and it will be able to use the older protocols again.

Example with TLSv1.1 removed:

jdk.tls.disabledAlgorithms=SSLv3, TLSv1, RC4, DES, MD5withRSA, \
DH keySize < 1024, EC keySize < 224, 3DES_EDE_CBC, anon, NULL, \

[spring boot tls 설정]
server.ssl.enabled-protocols=TLSv1.1+TLSv1.2
```