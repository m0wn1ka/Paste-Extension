# paste extension
## use case
- can be used to bypass  `pasting of data restrction`
## how it works
- when the paste event happens , some website write  a event listener and they block the paste operation
- this extension would add a event listner which would stop the event propagation
- so the restriction placed by website is bypassed, as the code which would stop pasting will not be executed

## for copy
```
function fixUserSelect() {
  for (const sheet of document.styleSheets) {
    // Some stylesheets may be cross-origin and not accessible
    try {
      for (const rule of sheet.cssRules) {
        if (rule.style && rule.style.userSelect === "none") {
          rule.style.userSelect = "auto";
        }
      }
    } catch (e) {
      // Ignore SecurityError for cross-origin stylesheets
      console.warn("Skipping stylesheet:", sheet.href, e);
    }
  }
}
fixUserSelect()
```
