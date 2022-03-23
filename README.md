# Inlineswap

A lightweight, minimally-invasive HTML preprocessor.

Inlineswap searches your HTML files for commands in the form of `<!-- COMMAND [ARGS] -->` and evaluates them IN-PLACE.  It is minimally-invasive because the "source" and the "output" is the same file, and the commands are just regular HTML comments, so if you wish to stop using Inlineswap, you can simply ignore or delete the commands and instead edit your files manually, or use any other HTML preprocessor.

The main purpose of Inlineswap is to automatically update headers and footers of websites that are hand-written static HTML.  Instead of manually copy&pasting the updates to the shared parts, Inlineswap allows you to use a directive like `<-- header --> ... <-- /header -->` (although "header" can be any word) in your main HTML page (e.g. `index.html`) to define the shared HTML block, and the directive `<-- get header from index.html --> ... <-- /get -->` in another HTML page, which tells Inlineswap to copy&paste the "header" block from index.html into that page.

Further documentation can be found in the comments of the "inlineswap" executable file.

## Security Warning

Another feature is running arbitrary shell commands and automatically inserting their output into your HTML file.  For example, you can use it to insert markdown content into your HTML files with this command: `<!-- run markdown my_content.md -->`.  For the sake of simplicity, the commands are not sandboxed or validated, which unfortunately turns this into a gaping security hole.  The best mitigation as of now is to manually review all "run" commands before running Inlineswap with a command like this:

    grep '<!-- run' *.html

## Who uses Inlineswap?

Inlineswap is used by https://ranger.github.io/ and you can take a peek at the HTML source code of the website to get some inspiration.

In general, though, I would only recommend using it for fast prototyping and not for serious projects, since it's rather limited, and the "run" command is platform-dependent (and a security nightmare).
