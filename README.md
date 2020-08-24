# DEPRECATED

This package was republished as [`jfmengels/elm-review-unused`](https://package.elm-lang.org/packages/jfmengels/elm-review-unused/latest/) in order to have a more consistent naming convention for `elm-review` rule packages.

To migrate, I recommend going to your review configuration and running the following commands:

```bash
# NOTE: You'll need to have Node.js installed to be able to use `npx`
npx elm-json uninstall jfmengels/review-unused --yes
npx elm-json install jfmengels/elm-review-unused --yes
```

# review-unused

Provides [`elm-review`](https://package.elm-lang.org/packages/jfmengels/elm-review/latest/) rules to detect unused elements in your Elm project.

## Provided rules

- [`NoUnused.Variables`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-Variables) - Reports unused top-level variables and types, imports and imported variables and types inside of a module.
- [`NoUnused.CustomTypeConstructors`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-CustomTypeConstructors) - Reports unused constructors for a custom type.
- [`NoUnused.Exports`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-Exports) - Reports unused exposed elements from a module.
- [`NoUnused.Modules`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-Modules) - Reports unused modules in the project.
- [`NoUnused.Dependencies`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-Dependencies) - Reports unused dependencies in the project.
- [`NoUnused.Parameters`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-Dependencies) - Report unused parameters.
- [`NoUnused.Patterns`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-Dependencies) - Report useless patterns and pattern values that are not used.

## Example configuration

```elm
module ReviewConfig exposing (config)

import NoUnused.CustomTypeConstructors
import NoUnused.Dependencies
import NoUnused.Exports
import NoUnused.Modules
import NoUnused.Parameters
import NoUnused.Patterns
import NoUnused.Variables
import Review.Rule exposing (Rule)


config : List Rule
config =
    [ NoUnused.CustomTypeConstructors.rule []
    , NoUnused.Dependencies.rule
    , NoUnused.Exports.rule
    , NoUnused.Modules.rule
    , NoUnused.Parameters.rule
    , NoUnused.Patterns.rule
    , NoUnused.Variables.rule
    ]
```


## How this package works

This package works by having several rules that check for different unused elements, and that complement each other.

This allows for fine-grained control over what you want the rules to do. If you add these rules to an existing project, you will likely get a lot of errors, and fixing them will take time. Instead, you can introduce these rules gradually in batches. For cases where the errors are too time-consuming to fix, you can ignore them in the configuration, until you take care of them.

A few of these rules provide automatic fixes using `elm-review --fix` or `elm-review --fix-all`.

## Thanks

Thanks to @sparksp for writing [`NoUnused.Parameters`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.5/NoUnused-Dependencies) and [`NoUnused.Patterns`](https://package.elm-lang.org/packages/jfmengels/review-unused/2.1.2/NoUnused-Dependencies).
