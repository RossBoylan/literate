# Change Log

## 0.14.4nostyle
  * Do not install the package style file.
  This change removes the contribution point for styles.css without removing the file
  itself from the source.  There remain lots of references to `./style.css`, all 
  generated from the template at line 2179 of `literate.literate`, I think.  We'll
  see how that works.  There are 2 problems with the previous style useage:
     1. It affects all files and projects, not just those using `literate`.
     2. It doesn't work well with some themes, in particular dark ones.

## 0.14.4

* Hide code comments from generated HTML ( #38 )

## 0.14.3

* Fix default HTML template by including proper doctype.

## 0.14.2

* Add simple mermaid.js support by the way of wrapping code from fences that
  express mermaid diagrams in `pre` tags with the class `mermaid`. ( #9 )
* Update (dev) dependencies

## 0.14.1

* Quick adaptations for support of v0.14.0 features, no functional changes.

## 0.14.0

* Add template support
  * HTML template file can be specified in code fence with info containing
    string `SETTINGS`. This code fence needs to be placed in `index.literate`. A
    default HTML template is baked into the extension. This can be overridden by
    specifying your own (#36 #6)
  * source template file can be specified on starred fragments after the dollar
    sign. Use `template=filename`
  * `SETTINGS` fence accepts now two keys: `template` and `authors`. The first
    takes a filename. The mentioned file has to exist for it to be actually
    used. `authors` can hold one or more author names separated by semi-colons

## 0.13.0

* Breaking change: Handle filenames on starred fragments better ( #34 )
  * Starred code fragments need to be changed to end in whitespace plus dollar
    sign to process properly with version 0.13.0 or later of this extension
  * Introduce diagnostics telling about missing filename
* Make EOL handling platform dependant instead of always forcing CRLF
  * Only on Windows `core.autocrlf true` should be set, on other platforms it
    should be set to `core.autocrlf false`

## 0.12.1

* Fix Split Fragment adding unnecessary space around language identifiers ( #32 )


## 0.12.0

* Emit error diagnostic when colon is missing from fragments ( #31 )

## 0.11.1

* Fix for bug #27. Only the first highlight was being handled in a fragment name
  tag. Now all highlights are cleaned up.

## 0.11.0

* Add styling for fragment names in code fences. Remove hljs highlighting tags
  from fragment names and wrap fragment name in span with CSS class
  literate-tag-name. Based on proposal #23 by Konrad Kleine
* Workspace settings and README tweaked after feedback from several users.
  README had PR #24 by Nicolas Lelong merged
* Added minimal CONTRIBUTING.md

## 0.10.1

* Fix error with LF to CRLF replacement

## 0.10.0

* Write out CRLF instead of LF

## 0.9.0

* Add reference provider, which allows to see where fragments are mentioned or
  used. This further improves the navigability of **literate** projects

## 0.8.0

* Add definition provider, which allows to quickly navigate to where the
  definition of a fragment is

## 0.7.0

* Add `literate.split_fragment` command. Splits the fragment the cursor
  currently is in on the next line. Resolves #17.
* Add browse capability for the literate fragment explorer.

## 0.6.1

* Fix #16 - inadequate copy&paste resulted in double definitions not being
  recognized.

## 0.6.0

* Add `literate.create_fragment_for_tag` command. When the cursor is on a
  fragment use in either a code fence or in a paragraph the command creates a
  new fragment definition after the block.
* Add code action provider that emits code actions with
  `literate.create_fragment_for_tag` so that these can be taken by doing quick
  fixes.
* Fix #14 - diagnostic message not precise enough for fragment not found.

## 0.5.0

* Add rename capability for fragments
* Parts have been deduplicated and centralized to make it even easier to add new
  providers in the future

## 0.4.1

* Overhauling literate file processing. There is now one class responsible for
  handling the parsing and rendering of literate files and for creation of
  fragment maps. Different parts use the new central fragment repository. This
  has been done with future enhancements in mind.
* Literate program split up into several documents. TOC, chapter linking and
  similar features have become important, but for now accept that browsing the
  literate program isn't the easiest. Something to be address better through #7,
  #10 and #11.
* Diagnostics don't repeat unnecessarily.

## 0.4.0

* Add hovers when mousing over fragment usage or fragment mention.

## 0.3.0

* Add code completion for code fragments. Typing an opening chevron `<` will
  show all code fragment names known in the current project.
* Completion item detail will show fragment code

## 0.2.4

* Rework introduction
* Improve explanation of high level mechanism of the extension
* Improve fragment regular expressions through using named groups
* Adapt top fragment diagnostic check to take into account named group
* Move to using space indentation, width 2

## 0.2.3

* Move error message from dialog to statusbar. In conjunction with the Problems
  view developers get currently enough information that is already properly
  integrated.

## 0.2.2

* Unbreak extension. Incorrect setup and general inadequate skill level caused
  the extension to no longer function correctly.

## 0.2.1

* Fragment explorer automatically updates on changes made to literate documents
* The `literate.process` command is executed on each literate document change
* Literate document parsing takes into account `TextDocument`s, that is
  documents in text editors that may have changes different from what is on
  disk. This can be especially useful with other extensions in use, like
  linting and lsp interaction

## 0.2.0

* Rewrite code to enable parsing and handling of fragments outside of the
  `literate.process` command
* Add rough version of the fragment explorer

## 0.1.8

* More literate text explaining the workings of the plug-in. Most of the new
  text is about fragments
* Don't bundle node_modules unnecessarily

## 0.1.7

* Add LICENSE file (MIT)
* Bump engines dependency to 1.63.2

## 0.1.6

* Minor fixups and dependency updates (dev)
* Ensure extension works with vscode 1.63.2

## 0.1.5

* Ensure `literate` can be created the literate way

## 0.1.4

* Package improvement was not working out correctly. Revert to old packaging
  mechanism

## 0.1.3

* Package improvement, no functional changes

## 0.1.2

* This time actually have syntax highlighting
  in the code fragments

## 0.1.1

* Keep syntax highlighting in generated HTML

## 0.1.0

* Resolve #3: Honor indentation in code fragments

## 0.0.9

* Resolve #2: Write out HTML files for literate programs
* Resolve #1: Don't add src in generated code file path

## 0.0.8

* Complex fragment setup saving was broken. Works again.

## 0.0.7

* Allow to specify file name on top code fragment. Use paths relative to the
  workspace. Subfolders can be part of the path. To save code for `<<Name of
  Fragment.*>>` to `CodeFile.cs` use:

~~~literate
```csharp : &lt;&lt;Name of Fragment.*&gt;&gt;= ./CodeFile.cs
// code here
```
~~~

## 0.0.6

* Make _all_ hljs classes black text by default for now

## 0.0.5

* Disable decorating generated code with #line

## 0.0.4

* Add Markdown contribution to render our code fences
* fragment tags are cleaned up from highlightjs rendering
* Start with simple styling using old white background with all black text

## 0.0.0 .. 0.0.3

* Simple code fragments through code fences (tripple backtick or tripple tilde)
* A code fence creates a new fragment on the info line
* A code fence extends an existing fragment on the info line
* Code fences/blocks reference fragments by using their tags
