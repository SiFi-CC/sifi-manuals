# Coding conventions

Coding conventions are described in coding_conventions.tex file. Generate output
with pdlatex:

    pdflatex coding_conventions.tex

All developers are obliged to follow them.

# Source code formatter.

The source code will be reformatted using the `clang-format`. The format rules
are inside `.clang-format` file in this repository. Copy or symlink the file
to the root directory of your project.

### 1. Manually invoking formatter

You can reformat file at any time using `clang-format`. The program check for
`.clang-format` file in the directory of teh file or any parent directory. That
is why we can put it just in the project root directory. Then invoke format with

    clang-format --style=file -i path/to/source/file.cc

Without `-i` option program will return to stdout the formatted code, with `-i`
it will update file in place.

### 2. When using KDevelop IDE

 1. Copy `format_source` to root directory of your project.
 2. Open Project Options and choose Source Formatter. Select C++ language and
    choose Custom Script Formatter and in the list select `kde_source_format`.
 3. The source formatting can be invoked by Edit->Reformat Source. It is
    suggested to assign a shortcut to the action, e.g. F2. Before each commit
    source should be reformatted.
 4. Parts of the code which should be excluded from formatting must be
    enclosed with `// clang-format off` and `// clang-format on` comments:

        void formatted_code;
        // clang-format off
            void    unformatted_code  ;
        // clang-format on