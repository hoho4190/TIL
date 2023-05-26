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
| Paste From History         | **⇧⌘V**        | **Ctrl+Shift+V**     |                    |

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

| name       | Expression | Default value | Skip if defined |
| ---------- | ---------- | ------------- | --------------- |
| DpName     |            |               |                 |
| MethodName | 아래 참고      | test          | V               |

```
regularExpression(regularExpression(DpName, "[\\(+\\)+\\[+\\]+\\:+]", ""), "((\\s)*(,+|\\s+|-+|_+)(\\s)*)+", "_")
```

#### Abbreviation: bddp

```java
@ParameterizedTest
@DisplayName("$DpName$")
@$Source$
void $MethodName$($Argument$) {
    // given
    $END$
    // when
    
    // then
}
```

| name       | Expression          | Default value | Skip if defined |
| ---------- | ------------------- | ------------- | --------------- |
| DpName     |                     |               |                 |
| Source     |                     |               |                 |
| MethodName | bdd의 MethodName과 동일 | test          | V               |
| Argument   |                     |               |                 |

#### Abbreviation: nestedc

```java
@Nested
@DisplayName("$DpName$")
class $ClassName$ {
    $END$
}
```

<table><thead><tr><th width="206">name</th><th width="425">Expression</th><th>Default value</th><th>Skip if defined</th></tr></thead><tbody><tr><td>DpName</td><td></td><td></td><td></td></tr><tr><td>ClassName</td><td>bdd의 MethodName과 동일</td><td>test</td><td>V</td></tr></tbody></table>

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

<table><thead><tr><th width="206">name</th><th>Expression</th><th>Default value</th><th>Skip if defined</th></tr></thead><tbody><tr><td>EXPR</td><td>variableOfType("")</td><td>"expr"</td><td></td></tr><tr><td>EXPR_COPY</td><td>escapeString(EXPR)</td><td></td><td>V</td></tr></tbody></table>

#### Abbreviation: ldmp

Description: Prints current method name, params, values to Logger

```java
log.debug($FORMAT$);
```

<table><thead><tr><th width="206">name</th><th width="354">Expression</th><th>Default value</th><th>Skip if defined</th></tr></thead><tbody><tr><td>FORMAT</td><td>아래 참고</td><td></td><td>V</td></tr></tbody></table>

```
groovyScript("'\"' + _1 + (_2.isEmpty() ? '' : ' - ' + _2.collect{it + ' = {}'}.join(', ')) + '\"' + (_2.isEmpty() ? '' : ', ' + _2.collect{it}.join(', ')) ", methodName(), methodParameters())
```

#### Abbreviation: ld, li, le
