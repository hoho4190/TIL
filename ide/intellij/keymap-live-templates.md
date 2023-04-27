---
description: 자주 사용하는 것 정리
---

# Keymap, Live Templates

## Keymap

| Name                       | Mac            | Windows              | etc   |
| -------------------------- | -------------- | -------------------- | ----- |
| Duplicate line             | **⌘D**         | **Ctrl+D**           |       |
| Delete Line                | **⌘Backspace** | **Ctrl+Y**           | ⇧+del |
| Move Line                  | **⌥⇧↑/↓**      | **Alt+Shift+↑/↓**    |       |
| Move Statement             | **⇧⌘↑/↓**      | **Ctrl+Shift+↑/↓**   |       |
| Optimize Imports           | **⌃⌥O**        | **Ctrl+Alt+O**       |       |
| Reformat Code              | **⌥⌘L**        | **Ctrl+Alt+L**       |       |
| Inline Variable            | **⌥⌘N**        | **Ctrl+Alt+N**       |       |
| Introduce Variable         | **⌥⌘V**        | **Ctrl+Alt+V**       |       |
| Introduce Parameter        | **⌥⌘P**        | **Ctrl+Alt+P**       |       |
| Complete Current Statement | **⇧⌘⏎**        | **Ctrl+Shift+Enter** |       |
| Run                        | **⌃R**         |                      |       |

## Live Templates

* sout
* soutf
* soutv
* soutp
* soutm

### Live Templates 추가

Abbreviation: bdd

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

| name       | Expression                                                      | Default value | Skip if defined |
| ---------- | --------------------------------------------------------------- | ------------- | --------------- |
| DpName     |                                                                 |               |                 |
| MethodName | regularExpression(spacesToUnderscores(DpName), "\__-\__", "\_") | test          | V               |
