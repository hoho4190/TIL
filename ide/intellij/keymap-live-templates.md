---
description: 자주 사용하는 것 정리
---

# Keymap, Live Templates

## Keymap

| Name                       | Mac            | Windows              | etc                |
| -------------------------- | -------------- | -------------------- | ------------------ |
| Duplicate line             | **⌘D**         | **Ctrl+D**           |                    |
| Delete Line                | **⌘Backspace** | **Ctrl+Y**           | ⇧+del              |
| Move Line                  | **⌥⇧↑/↓**      | **Alt+Shift+↑/↓**    |                    |
| Move Statement             | **⇧⌘↑/↓**      | **Ctrl+Shift+↑/↓**   |                    |
| Optimize Imports           | **⌃⌥O**        | **Ctrl+Alt+O**       |                    |
| Reformat Code              | **⌥⌘L**        | **Ctrl+Alt+L**       |                    |
| Inline Variable            | **⌥⌘N**        | **Ctrl+Alt+N**       |                    |
| Introduce Variable         | **⌥⌘V**        | **Ctrl+Alt+V**       |                    |
| Introduce Parameter        | **⌥⌘P**        | **Ctrl+Alt+P**       |                    |
| Complete Current Statement | **⇧⌘⏎**        | **Ctrl+Shift+Enter** |                    |
| Go to Test                 | **⇧⌘T**        | **Ctrl+Shift+T**     |                    |
| Run                        | **⌃R**         | **Shift+F10**        |                    |
| Resent Files               | **⌘E**         | **Ctrl+E**           | **⌘E⏎ - 이전 파일 이동** |

## Live Templates

* sout
* soutf
* soutv
* soutp
* soutm

### Live Templates 추가

#### Abbreviation: bdd

```java
@Test  
@DisplayName("$DpName$")  
void $MethodName$() {  
	// given  
	$END$  
	// when  
	  
	// then  
}
```

| name       | Expression                                                                                                     | Default value | Skip if defined |
| ---------- | -------------------------------------------------------------------------------------------------------------- | ------------- | --------------- |
| DpName     |                                                                                                                |               |                 |
| MethodName | regularExpression(regularExpression(DpName, "\[\\(+\\)+\\\[+\\]+]", ""), "(\s)_(,+\|\s+\|-+\|\_+)(\s)_", "\_") | test          | V               |

#### Abbreviation: nestedc

```java
@Nested
@DisplayName("$DpName$")
class $ClassName$ {
    $END$
}
```

| name      | Expression                                                                                                     | Default value | Skip if defined |
| --------- | -------------------------------------------------------------------------------------------------------------- | ------------- | --------------- |
| DpName    |                                                                                                                |               |                 |
| ClassName | regularExpression(regularExpression(DpName, "\[\\(+\\)+\\\[+\\]+]", ""), "(\s)_(,+\|\s+\|-+\|\_+)(\s)_", "\_") | test          | V               |

#### Abbreviation: ld, li, le

```java
log.debug($END$);
// log.info($END$);
// log.error($END$);
```

#### Abbreviation: ldv, liv, lev

```java
log.debug("$EXPR_COPY$ = {}", $EXPR$);
// log.info("$EXPR_COPY$ = {}", $EXPR$);
// log.error("$EXPR_COPY$ = {}", $EXPR$);
```

| name       | Expression         | Default value | Skip if defined |
| ---------- | ------------------ | ------------- | --------------- |
| EXPR       | variableOfType("") | "expr"        |                 |
| EXPR\_COPY | escapeString(EXPR) |               | V               |
