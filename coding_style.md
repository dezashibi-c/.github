# My Preferred Coding Style and Guidelines

This document outlines my personal coding style preferences, which are influenced by widely accepted conventions in the C programming community.

## Comments

I generally avoid excessive comment blocks at the top of files unless necessary. However, it is good practice to include a comment block with useful information at the beginning of each file. Here is a template I often use:

```c
// ***************************************************************************************
//    Project: 
//    File: 
//    Date: 
//    Author: 
//    Contact: 
//    Website: 
//    License:
//     Please refer to the LICENSE file, repository, or website for more information about
//     the licensing of this work. If you have any questions or concerns,
//     please feel free to contact me at the email address provided above.
// ***************************************************************************************
// *  Description: 
// ***************************************************************************************
```

## Naming Conventions and Styles

- **Variables:** Use snake_case, e.g., `my_variable`.
- **Function Names:** Use snake_case, e.g., `my_function`.
- **Custom Types:** Use PascalCase, e.g., `MyType`, `MyStruct`, `MyEnum`.
- **Constants and Enum Values:** Use ALL_CAPS, e.g., `PI`, `THING`, `SATURDAY`.
- **Function Macros:** Can be written in lowercase like normal functions.
- **Scope and Purpose in Naming:** Begin with the scope and purpose in function names:
  - e.g., `file_get_extension()`
  - This applies to both functions and function macros.
- **Avoid Function Pointers in Structs:** Do not use function pointers in structs to mimic C++ object-oriented programming. Instead, use proper functions:
  - e.g., `my_type_create`
  - e.g., `my_type_get_whatever_data`
  - e.g., `my_type_delete`
  - Also, don't hesitate to use some macros to simplify code where appropriate.
- I would prefer to connect `*` to the types when defining theme and never use multiple definition to prevent stupid problems
  - Types like `char*`, `int*`, `MyStruct*` are way more readable to me than I put `*` close to the variable name
  - I don't like multiple definitions for pointers in one go, I prefer to define pointers in separate lines with proper initializations and other stuffs.
- I prefer to continue the old-school way of putting '{' and '}' in separate lines. when I'm writing `C` I can't help myself but seeing the code like that.
- I prefer using 4 spaces for indentations.

## Good advices from good people

[Chris Wellons](https://nullprogram.com) also known as [skeeto](https://github.com/skeeto) has some good advices on [his blog](https://nullprogram.com/blog/2023/10/08/) about his style:

For example **Primitive Types** section not only allows you to write more readable code also it amazingly increases your code portability, don't forget to include `stdint.h` by the way.

```c
typedef uint8_t   u8;
typedef char16_t  c16;
typedef int32_t   b32;
typedef int32_t   i32;
typedef uint32_t  u32;
typedef uint64_t  u64;
typedef float     f32;
typedef double    f64;
typedef uintptr_t uptr;
typedef char      byte;
typedef ptrdiff_t size;
typedef size_t    usize;
```

Or some standard `Macros` such as `countof` or `lengthof`, I think it worth reading, please do ⭐!

## My Vscode Config

```js
{
    BasedOnStyle: LLVM,
    UseTab: Never,
    IndentWidth: 4,
    TabWidth: 4,
    BreakBeforeBraces: Allman,
    AllowShortIfStatementsOnASingleLine: false,
    IndentCaseLabels: false,
    ColumnLimit: 0,
    AccessModifierOffset: -4,
    NamespaceIndentation: All,
    FixNamespaceComments: false,
    PointerAlignment: Left
}

```

- Get used to writing document comment block for functions and function macros like this:

```c
/**
 * @brief a brief description of what it does
 *
 * This macro of function ......
 * .... rest of the more detailed description.
 *
 * @param param description of the parameter.
 * @return description of function return.
 */
```

## Should I use libs by others?

That's a tough question to answer to be honest but I personally have my own answer that works for me, so I'm going to share it with you the dear reader.

- I always start with the answer "No" then I go to the following process
- I search to see if there is any similar work done
- If Yes:
  - First license:
    - I never argue over giving attribution and I think in my idea giving attribution is a must even if the programmer didn't ask for it.
    - If I'm almost sure I might use my work in a commercial way in any possible way I just quickly check to see if the license is `GPL` based and I quickly close the browser tab if so.
    - I prefer MIT Licenses, BSD and Apache are good as well. I respect `Public Domain` and `UnLicence` projects, and I try to go for them first and if I can I would support them, why not.
  - Second implementation:
    - Over-complication is not my cup of tea.
    - Bundling too many things together is my enemy.
    - I really prefer two file projects (one header and one implementation) even more than single header one. but single header project works for me too.
    - If that's almost close to what I've had in mind then why bother, I go for it. I'm not suffering from masochism to redundantly implement everything by myself.
      - **IMPORTANT TIP HERE:** That's true only when it's not a over-complication, badly crowded, hard to debug project.
    - I would prefer to see my preferred conventions as well but if the criteria mentioned previously are met it's not a big deal just to fork the project and change it to my taste.
- So that's when I say yes use third party libraries.

## License

Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)

Copyright (c) 2024 Navid Dezashibi <navid@dezashibi.com>. All rights reserved.

By exercising the Licensed Rights (defined below), You accept and agree to be bound by the terms and conditions of this Creative Commons Attribution-NonCommercial 4.0 International Public License ("Public License"). To the extent this Public License may be interpreted as a contract, You are granted the Licensed Rights in consideration of Your acceptance of these terms and conditions, and the Licensor grants You such rights in consideration of benefits the Licensor receives from making the Licensed Material available under these terms and conditions.

You are free to:

- Share — copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material

Under the following terms:

- Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
- NonCommercial — You may not use the material for commercial purposes.

No additional restrictions — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

Full license: <https://creativecommons.org/licenses/by-nc/4.0/>
