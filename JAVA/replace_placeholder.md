### placeholder 치환 (${...})
- https://github.com/eugenp/tutorials/blob/master/core-java-modules/core-java-regex-2/src/test/java/com/baeldung/replacetokens/ReplacingTokensUnitTest.java
```
    @Test
    public void escapeRegexCharacters() {
        Pattern regexCharacters = Pattern.compile("[<(\\[{\\\\^\\-=$!|\\]})?*+.>]");

        assertThat(replaceTokens("A regex character like [",
          regexCharacters,
          match -> "\\" + match.group()))
          .isEqualTo("A regex character like \\[");
    }

    @Test
    public void replacePlaceholders() {
        Pattern placeholderPattern = Pattern.compile("\\$\\{(?<placeholder>[A-Za-z0-9-_]+)}");

        Map<String, String> placeholderValues = new HashMap<>();
        placeholderValues.put("name", "Bill");
        placeholderValues.put("company", "Baeldung");

        assertThat(replaceTokens("Hi ${name} at ${company}",
          placeholderPattern,
          match -> placeholderValues.get(match.group("placeholder"))))
          .isEqualTo("Hi Bill at Baeldung");
    }
```