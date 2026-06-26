# Find Theme Keys

Discovering theme keys can be a very tedious process as a theme creator. Unfortunately, there
is no single convenient place that lists them all. So you will need to find the keys yourself.
Hopefully, this guide will help ease the process.

Here are methods for discovering theme keys.

## UI Inspector

Use [UI Inspector](https://plugins.jetbrains.com/docs/intellij/internal-ui-inspector.html) to find information about
a specific UI element (including colors/keys) in the IDE. Works just like the color picker.

**Requirement:**

- Enable [Internal Mode](https://plugins.jetbrains.com/docs/intellij/enabling-internal.html)

## LaF Defaults

Provides a list of defaults for almost all theme keys that exists in the currently running IDE. Only
shows **runtime theme keys
**. [Look and Feel (LaF)](https://plugins.jetbrains.com/docs/intellij/internal-ui-laf-defaults.html)

**Requirement:**

- Enable [Internal Mode](https://plugins.jetbrains.com/docs/intellij/enabling-internal.html)

## Theme metadata JSON

A JSON containing a reference to **supported**, **documented**, and **exposed** metadata theme keys
from the official JetBrains
repo. [IntelliJPlatform.themeMetadata.json](https://github.com/JetBrains/intellij-community/blob/master/platform/platform-resources/src/themes/metadata/IntelliJPlatform.themeMetadata.json)

## IntelliJ Source

By far the most tedious, yet most resourceful method!

Search the official source code at [
`JetBrains/intellij-community` repository](https://github.com/JetBrains/intellij-community) for theme keys. The theme
keys
found here includes **keys that are not present in any of the other methods**.

### Keywords

Theme keys can easily be found using the following keywords:

- `UIManager.getColor(`
- `JBColor.namedColor(`
- `JBUI.get`

#### Search by theme key name

You can also search by find the name of the theme key you are looking for. Ex: `.foreground`,`Link.`,
`.inactiveBackground`

#### Search JBUI.CurrentTheme

Another method is searching with keyword: `JBUI.CurrentTheme`.

Example:
Let's say you search `JBUI.CurrentTheme` and you get the following:

```java
myLabel.setForeground(JBUI.CurrentTheme.Popup.headerForeground(active));
```

This translates to `Popup.Header.activeForeground`.

## Code Completion

For this method, you rely on IntelliJ's autocomplete feature. Type a few words and intelliJ gives you
valid theme key options to complete the phrase. **Be warned, IntelliJ recognizes some valid theme keys as
being incorrect when it's not.** For instance, `EditorTabs.inactiveUnderlinedTabBorderColor`.


