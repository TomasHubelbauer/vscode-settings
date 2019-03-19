# VS Code Settings

These are my settings for VS Code.

Place `'{\n' + [...document.querySelectorAll('code, pre')].filter(codeOrPre => codeOrPre.previousSibling === null).reduce((json, codeOrPre) => json + codeOrPre.textContent.split('\n').map(line => '  ' + line).join('\n') + ',\n', '') + '}\n'` to this page's developer tools console to get the full JSON.

I am using the default Windows shell - PowerShell.

`"terminal.integrated.rendererType": "dom"`

I am using the DOM rendered type for performance and as a matter of principle - using `canvas` to reimplement DOM is dumb.

`"git.autofetch": true`

Self-explanatory.

`"git.confirmSync": false`

This is to get rid of an annoying Git question if I really want to pull & push. Yeah I do.

`"explorer.confirmDragAndDrop": false`

This also hides an annoying question. I want to drag & drop and if I made a mistake, I can just revert it by hand.

`"typescript.updateImportsOnFileMove.enabled": "always"`

I always want VS Code TypeScript language service to rewrite my `import` paths when I move files around.
If it makes a mistake, TypeScript will fail to compile and I will notice and fix it.

`"breadcrumbs.enabled": true`

I have written an extension to do this before and now it is a part of VS Code, so of course I am going to enable it. :-)
I think this should be on by default.

`"explorer.confirmDelete": false`

VS Code moves files to the Recycle Bin by default so there is no risk in not asking to delete stuff.
Additionally, I disable Recycle Bin on Windows, so I am taking a risk here, but it's an acceptable level of risk for me.

`"editor.rulers": [ 80, 120 ]`

I have a widescreen monitor and 80 is an outdated line length anyway, but I don't believe lines should take up the width
of the screen because it hurts readability. There is research out there which finds 70-100 characters per line to be best
for comprehension speed. I think it's still too little so I have settled on 20 after collecting my own anecdata.

`"editor.tabSize": 2`

The only reasonable tab setting.

`"workbench.settings.editor": "json"`

I will resist the UI editor for settings in VS Code until the end of my days.
Additionally, I will never accept a UI settings editor which is not fully generated based on extensions' contributions.
The current half-way between some hard-coded parts and other poorly generated parts is IMO a dead end and dumb.

`"workbench.settings.useSplitJSON": true`

This will probably be soon removed, but I use and like the split JSON editing experience and will be pissed when they take it.

`"html.format.extraLiners": ""`

This is an example of super daft behavior in VS Code and probably other software. Do not place blank lines atop any elements.

`"html.format.indentInnerHtml": true`

This is to prevent one of the daftest behavior of all time, to not indent `head` and `body` in HTML.
I remember this going back to I think FrontPage days, certainly Visual Studio proper does it, and there's probably more examples
before my time or in software I do not use.
And this is the wrong behavior always, in any case. There is no need to special-case these elements, just indent them.

`"editor.formatOnSave": true`

Goes without saying.

`"git.rebaseWhenSync": true`

Related to my Git configuration whhich I keep in another repository of mine.

`"window.restoreWindows": "none"`

Restoring the last window is actually quite handy 99 % of the time, but when it's not what I want, VS Code takes too much
time loading extensions and services before it becomes responsive enough for me to close the existing workspace and get to
the start page. And I also just don't like the feeling of starting with a dirty workspace anyway. So no restoration for me.

This will still open two windows when there was an unsaved file in a window that got closed. I haven't looked into how to
prevent that.

```json
"files.exclude": {
  "**/.git": true,
  "**/.svn": true,
  "**/.hg": true,
  "**/CVS": true,
  "**/.DS_Store": true,
  "node_modules": true
}
```

This is here just for the `"node_modules": true` line, the rest is there by default. I do not mind having `node_modules`
in the workspace for the odd case where I want to change something in a module to try something or another. But my main
beef with VS Code regarding `node_modules` is that it will expand whatever path to a typings file when I do Ctrl+click
to go to a TypeScript definition. So I always have `node_modules` expanded which makes the Explorer pane useless. I have
no option but to hide it then. I wish there was a different setting, something like `expand.exclude`.

`"html.format.wrapLineLength": 0`

This prevents Code from wrapping HTML lines that are too long by breaking them up and wrapping the attributes.
I find the results almost always ugly and they usually are caused by long `a` elements with long links in `href` which is something
I am perfectly comfortable with not getting wrapped.
