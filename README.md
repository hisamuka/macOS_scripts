## Things to do after installing Mac OS

- Copy the fonts from ./fonts to ~/Library/Fonts/


#### Manual Installation
- Setting up the developing environment
    + Install xcode
    + brew install gcc
    + brew install g++
    + brew install openblas
    + brew install libomp # openmp - https://iscinumpy.gitlab.io/post/omp-on-high-sierra
        + it requires the compilation flag -Xpreprocessor -fopenmp for the source and -Xpreprocessor -fopenmp -lomp to compile the programs.


- brew install rename # install rename unix command
- Install iTerm
    + Remove dimming from inactive panes
        + iTerm2 > Preferences > Appearance
        + Select: Dim inactive split panes

    + Add custom colors, shortcuts, etc, in your Profile:
        + iTerm2 > Preferences > Profile (edit or create a new profile)
            + On General
                + Open tab and panes in the same directory
                    + Click on Working Directory > Advance
                    + Click on Working Directory for New Split Panels > Reuse previous session's directory
                    + Source: https://coderwall.com/p/9xo7aq/open-up-iterm2-splits-in-current-working-directory
            + On Colors
                + change the Basic Colors - Foreground to white
            + On Text
                + Change Font to 16pt Monaco
            + On Keys
                + Use ⌥ ← and ⌥→ to jump forwards / backwards words in iTerm 2, on OS X
                    + First you need to set your left ⌥ key to act as an escape character (Esc+): Settings > Profile > Keys > Left option as +Esc
                    + Second you need to either locate the current shortcut for ⌥ ← or create a new one, in the Profile Shortcut Keys, with the following settings:
                        + Keyboard Shortcut: ⌥←
                        + Action: Send Escape Sequence
                        + Esc+: b
                    + Third, repeat for the ⌥→ keyboard shortcut with the following settings:
                        + Keyboard Shortcut: ⌥→
                        + Action: Send Escape Sequence
                        + Esc+: f
                    + Source: https://coderwall.com/p/h6yfda/use-and-to-jump-forwards-backwards-words-in-iterm-2-on-os-x
                + Pane Navigation shortcuts:
                    + Keyboard Shortcut: ^Tab (ctrl + tab)
                    + Action: Next Pane
                    
                    + Keyboard Shortcut: ^ShiftTab (ctrl + shift + tab)
                    + Action: Previous Pane

    + To avoid pressing tab twice for autocomplete, we put the line below into the ~/.inputrc
        set show-all-if-ambiguous on

    + Custom .profile (equivalent to the .bashrc from Linux)
        os/.profile

    + Change the prompt display:
        + Put the following commands into ~/.profile (there is no ~/.bashrc in newest Mac OS)
            + PS1='\u@\h:\w\$ '
    + Put color on prompt:
        + http://blog.taylormcgann.com/tag/prompt-color/
        + To color code your prompt on a Mac, use the following template:
            + \[\033[COLOR_CODE_HERE\]PROMPT_ESCAPE_OR_TEXT_HERE\[\033[0m\]
        + Here’s a comprehensive list of color encoding:
        ```
        # Regular Colors
        \[\033[0;30m\] # Black
        \[\033[0;31m\] # Red
        \[\033[0;32m\] # Green
        \[\033[0;33m\] # Yellow
        \[\033[0;34m\] # Blue
        \[\033[0;35m\] # Purple
        \[\033[0;36m\] # Cyan
        \[\033[0;37m\] # White

        # High Intensty
        \[\033[0;90m\] # Black
        \[\033[0;91m\] # Red
        \[\033[0;92m\] # Green
        \[\033[0;93m\] # Yellow
        \[\033[0;94m\] # Blue
        \[\033[0;95m\] # Purple
        \[\033[0;96m\] # Cyan
        \[\033[0;97m\] # White

        # Background
        \[\033[40m\] # Black
        \[\033[41m\] # Red
        \[\033[42m\] # Green
        \[\033[43m\] # Yellow
        \[\033[44m\] # Blue
        \[\033[45m\] # Purple
        \[\033[46m\] # Cyan
        \[\033[47m\] # White

        # High Intensty backgrounds
        \[\033[0;100m\] # Black
        \[\033[0;101m\] # Red
        \[\033[0;102m\] # Green
        \[\033[0;103m\] # Yellow
        \[\033[0;104m\] # Blue
        \[\033[10;95m\] # Purple
        \[\033[0;106m\] # Cyan
        \[\033[0;107m\] # White

        #Replace any leading leading 0; with 1; for bold colors
        #Replace any leading 0; with 4; to underline
        ```

- Configure Sublime Text
    - Install My Workspace (Colors, keys, snippets, ...)
        + bash my_sublime_settings.sh

    - Install Package Control https://sublime.wbond.net/installation
    - Then, to install a package: On Sublime, press ctrl+shift+p, install Package and select the package
    
    - Some packages to install:
        - SideBarEnhancements
        - Alignment: ctrl+alt+a to align
        - BracketHighlighter
        - AStyleFormatter - ctrl+alt+f para alinhar todo o arquivo, ctrl+k+f para alinhar um trecho selecionado
        - Cython
        - LateXTool
            + It's required to install: latexmk
            + After Installing, Reconfigure LatexTools
                * Preferences > Package Settings > LatexTools > Reset user setting to default
            + Edit custom settins in Preferences > Package Settings > LatexTools > Settings User:
                * "keep_focus": false,
                * "display_log" : true,
                * "ref_add_parenthesis": true
                * "env_auto_trigger": true,
        - LaTeX-cwl
        - Git
        - Valgrind
        - Trimmer: helps you remove unnecessary spaces, as well as trailing spaces
        - Markdown Preview
        - FileDiffs:  allows you to see the differences between two files in SublimeText
        - C++11
        - Aligntab: aligns by : ; , .
        - Anaconda (python programming)
            + Set in the anaconda default config: "pep8": false 
        - VCSGutter (enables some symbols aside of the code to indicate SVN changes)
        - JsonLint
        - Fold Comments
            - Go to Preferences > Package Settings > Fold Comments > Key Bindings - Default
            - Set: ctrl+. to fold/unfold all comments in the text
        
        - Clang-Complete (Auto completion to C/C++)
            - https://packagecontrol.io/packages/Clang-Complete
            - From package control (only supported on Mac)
                + Clang-Complete
            - Go to the configuration file in *~/.config/sublime-text-3/Packages/Clang-Complete/cc.sublime-settings* and add the following content
            ```
            "additional_language_options":
            {
                // For example, you can use "c++": ["-std=c++11"] to enable C++11 features.
                "c++" : ["-std=c++11"],
                "c": ["-std=c11"],
                ...

                // in include_options, I`ve just added the line below
                "-isystem", "/Library/Developer/CommandLineTools/usr/lib/clang/8.0.0/include/",
            },
            ```
            - In the configuration file of the projects, paste the settings available in ./sublime/ift.sublime-project
                + I have to add a lot of include paths to avoid errors
        For Web
        - LiveReload - realoads the web page automatically after saving the source.
        - ColorHighlighter
        - AutoFileName
        - CSScomb // code style formatter
        - Bootstrap3 Snippets
        - Sass
        - jQuery
        - jQuery Snippets pack
        - PHPIntel
        - CSS Snippets
        - CSS Completions
        - CSS3
        - HTMLAttributes
        - HTML Snippets
        - HTMLBeautify
        - Emmet - several snippets for web development
        - LiveStyle - Live bi-directional CSS edit of new generation
                    - if you edit the css by the browser, it is edit in the source file
        - HTML5 - snippets and bundlers for HTML5
        - MarkdownEditing
        - MarkdownPreview
        - MarkdownLivePreview






