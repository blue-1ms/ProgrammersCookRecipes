# How to Contribute

## Introduction

Just modify/add the cooking guide and submit a Pull request.

When writing a new recipe, please copy and modify an existing template: [Sample recipe](./dishes/template/示例菜/示例菜.md)。

We recommend reading the repository's [Code of Conduct] before contributing (./CODE_OF_CONDUCT.md)。

## Content Specification

Recipe submitters **not required** to read this content specification. The following content has been included in the sample template in a concise and understandable manner. The maintainers of the project will make suggestions in your PR and assist with changes.

The Motivation of this project requires recipes to meet the following specifications, and recipes that do not meet the specifications will not be merged into the codebase. The maintainers of the project maintain this document as a formal standard and consensus.

- Each recipe should contain at least three parts: `raw materials and tools`, `calculation`, `operation`.

'Ingredients and tools' should list all the raw materials and utensils required for this dish except the 'imaginary prepared items'.
`Calculation` should quantify the amount of raw materials required for the dish. (regardless of whether it is related to the number of people)
`Operation` should describe the steps for preparing the dish.

- The preparation steps of the dish should be clear (non-ambiguous, non-ambiguous) and as accurate as possible. Ambiguous descriptions are not acceptable, while inaccurate or imprecise descriptions are acceptable.

> Inaccurate recipes will lead to slight deviations in the taste of dishes, and unclear recipes will lead to obvious anxiety of the cook.

Example: Ambiguous description

````
# Explanation: The description of the amount of salt here is ambiguous.
# Because for a certain amount of salt, the user cannot draw a definite objective conclusion: whether this amount is "small" or not.
add a pinch of salt

Add a few drops of oyster sauce
Heat the pan to eighth
Sprinkle a little chopped green onion
Cook until the chicken is broken
````

Example: unambiguous description

````
# Explanation: The description of the temperature of the pot here is inaccurate (it could be anything around 200 degrees Celsius), but the description is unambiguous.
# Because for a certain state of the pot, the user can perform a water drop test and draw a definite objective conclusion: this state either meets the requirements or does not meet the requirements.
Heat the pot until "when a few drops of water are added, the water droplets roll quickly on the pot without sticking"
Heat the pan until the Leidenfrost phenomenon is observed

Add 5ml soy sauce
wait until the water boils
Continue to cook until half of the soup remains
Fry until golden brown
Continue to fry for two minutes

# The amount of egg liquid that the ingredients may adhere to is determined
Coated with egg wash

# The amount of chopped green onion to be used has been mentioned in 'Calculation'
sprinkle with chopped green onion
````

Considering practical factors, some factors that are really difficult to clearly describe in the home kitchen can be excluded as special cases. E.g

````
# When describing the flame intensity of a gas stove
Slow fire, small fire, medium fire, large fire, etc.
# when describing colors
golden yellow etc.
# when describing hardness
become softer
````

- The `production steps` of the dish should be complete. This means that after performing all the operating steps, the dish has been completed.

- The 'raw materials and tools' of the dish should be complete. This means that items not mentioned in 'Materials and Tools' are not used when performing the steps.

## Notes for auditors

The content below is for reference only by those involved in the approval of recipes.

When approving, the most important thing is to avoid ambiguity: to ensure that there is as little flexibility as possible in accordance with his recipe. All ambiguities are to be pointed out. That is, whether it is a master chef or a newbie, as long as you follow the recipe, the effect should be exactly the same.

- Absolutely no room for flexibility in the recipe. The chef is not allowed to decide the amount to be added. `Appropriate amount` `Small amount` is not allowed
- Steps that allow chefs to make their own decisions are absolutely not allowed. For example: `You can adjust the cooking time according to your own preferences` such statements
- For a single object with a huge difference in size, volume and weight, it is not allowed to use it as a constraint, and an additional weight g must be marked
- The scoop is not a reliable unit. It is recommended to change to ml ml
- Make sure file paths are reasonable, file references are correct, no meaningless files are checked in
- The description of garlic, referring to three heads or three cloves may lead to ambiguity
- Allow `big fire` `medium fire` `small fire`
- Any punctuation marks, such as commas, require additional confirmation whether `replaceable or`, or `must be added together with `
- If a raw material is only counted once, but referenced multiple times, it must be additionally confirmed the amount of each reference
- Make sure he updates the Readme reference to his recipe before merging, if he is adding a new recipe
- Make sure he doesn't break the primary and secondary header formatting of the template
- Make sure he doesn't delete the required content in the template
- make sure he deletes the comments in the template
- Make sure the classification is correct and does not duplicate the name of an existing dish
- Make sure everything you check in is compliant with the CC0 protocol. Pay special attention to whether the picture has a watermark!
- Make sure he doesn't check in any personally identifiable information, EUII, Email address, GitHub username

## Documentation website building

In addition to directly deploying the HTML of `README.md`, you can also use `mkdocs-material` to render markdown files. This results in a prettier page.

Requirements: Python > 3.6

### debugging

```bash
pip install -r requirements.txt
mkdocs serve
```

Can be opened locally at <http://localhost:8000/>.

### compile

```bash
mkdocs build --strict
```

Generates static HTML pages, which exist in the `site/` folder. When hosting, point to `site/index.html`.

> **_Note:_**
> Since `mkdocs` does not natively support `*.md` in the root directory, you can only add the `mkdocs-same-dir` plugin as a workaround.
> Usually mkdoc will automatically check various files (eg *.jpg) in the folder and generate corresponding links. due to this
> workaround, now only `.md` files can be detected in the root directory. This restriction does not affect the rest of the folders (like `tips` and `dishes`).

## manual lint

If you need to check for irregularities in the documentation, you can run a lint operation manually.

Requirements: Ruby

### Install markdownlint

```bash
sudo gem install mdl # Linux
```

```powershell
gem install mdl # Windows, with administrators permission.
```

### Run lint

```bash
mdl . -r ~MD036,~MD024,~MD004,~MD029
```

## Generate Readme and mkdocs

In general, Readme and mkdocs files are automatically generated every time the master branch is changed. However, in some cases the developer may be required to generate these files manually.

Requirements: node, npm

```bash
node ./.github/readme-generate.js
```

## Automatic markdown fixes

The framework supports some automatic markdown bugfixes. In general, every time the master branch changes, it will be automatically corrected. However, in some cases manual corrections by the developer may be required.

Requirements: node, npm

```bash
npm install
./node_modules/.bin/textlint . --fix
```
