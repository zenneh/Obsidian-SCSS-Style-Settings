# Obsidian Style Settings SCSS
Generate the Obsidian Style Settings with SCSS.

```scss
@use "style-settings.scss" as ss;

$settings: (
    ss.CreateClassToggle("glassMorphism", "Glassmorphism", "Add glassmorphism to your theme")
);

$settings: ss.generateSettings($settings);

/* @settings

name: [Theme name]
id: [Theme id]
settings:
#{$settings}
*/
```

## Usage
The style settings function `generateSettings()` expects a map of components. 
This generates a scss string wich can be used inside the comment variable.

For a reference, check out the official Obsidian style settings repo
- https://github.com/mgmeyers/obsidian-style-settings 

<details>
<summary>
Components
</summary>

## Components
### Heading
`CreateHeading($id, $title, $description, $level: 1, $collapsed: true)`
### Class Toggle
`CreateClassToggle($id, $title, $description)`
### Class Select
`CreateClassSelect($id, $title, $description, $default, $options, $allowEmpty: false)`
### Variable Text
`CreateVariableText($id, $title, $description, $default)`
### Variable Number
`CreateVariableNumber($id, $title, $description, $default, $format: px)`
### Variable Number Slider
`CreateVariableNumberSlider($id, $title, $description, $default, $min, $max, $step: 1, $format: px)`
### Variable Select
`CreateVariableSelect($id, $title, $description, $default, $options)`
### Variable Color
`CreateVariableColor($id, $title, $description, $default, $options, $opacity: false, $format: hex)`
</details>


## Creating Components with options
### Normal options
```scss
@use "style-settings.scss" as ss;

$settings: (
    ss.CreateVariableSelect("theme-name", "Theme name", "Select theme name", (
        ss.CreateOption(
            "[value]": "[label]"
        )
    ))
);

$settings: ss.generateSettings($settings);

/* @settings

name: [Theme name]
id: [Theme id]
settings:
#{$settings}
*/
```

*! The label is optional in this component*
### Color options
```scss
@use "style-settings.scss" as ss;

$settings: (
    ss.CreateHeader("[id]", "[name]", "[Description]", 1, false),
    ss.CreateVariableSelect("[id]", "[name]", "[description]", (
        ss.CreateColorOption(
            "[id]": "[format]"
        )
    ))
);

$settings: ss.generateSettings($settings);

/* @settings

name: [Theme name]
id: [Theme id]
settings:
#{$settings}
*/
```