# Colors on Toril

## Terminal support

Toril supports three color terminal types:

* True color (16 million colors)
* Xterm-256 (256 colors)
* ANSI (16 colors)

The MUD will handle downgrading colors for players using older clients. In general, you should design with the full color options available
in True color, but check to make sure that they still look good on less capable clients. To verify colors in all terminal types, use the `color <msg>` command.

## Markup format

All color and formatting commands are wrapped inside of double curly braces.

```
{{red}}The quick brown fox jumped over the lazy dog.{{/red}}
```

Colors can be normalized with a specific end tag, like `{{/red}}`, or a generic version: `{{/}}`. You also don't have to use an end tag at all, and the system will insert one at the end of the line for you.

```
The quick {{orange}}brown fox{{/}} jumped over the lazy dog.
{{blue}}The quick brown fox jumped over the lazy dog.
The quick brown {{red}}fox{{/}} jumped over the lazy dog.
```

## Using colors

There are two ways to use colors: by name, or hex code. These two examples will have the same result:

```
{{goldenrod}}The quick brown fox jumped over the lazy dog.
{{#daa520}}The quick brown fox jumped over the lazy dog.
```

Toril supports the same named colors found in CSS3, but to really take advantage of all the colors available you'll want to use hex codes. If you're familiar with web development you'll recognize these hex codes from CSS.

* **Supported color names**: https://en.wikipedia.org/wiki/Web_colors#X11_color_names.
* **Hex code color picker**: https://encycolorpedia.com/

## Formatting commands

Toril supports several built-in commands that can make creating interesting color effects without a lot of manual work. These commands are used just like colors, but support multiple parameters separated by spaces. Example:  `{{alternate red green 4}}`

### Base

Sets the base color for this line of text. The base color is the color that will be used when the
color is normalized.

**Syntax**:

`{{base [color]}}`

**Example**
```
{{base coral}}The quick {{#c3c3c3}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_cmd_base.png)

### Background

Sets the background color.

**Syntax**:

`{{bg [color]}}`

**Example**
```
{{bg white}}{{red}}The quick brown fox jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_cmd_bg.png)

### Lighten

Lighten the color by a percentage. If the color is omitted, it will use the last used color instead.

**Syntax**:

`{{lighten [color1] [x]}}`

**Example**
```
{{lighten red 50}}The quick brown fox jumped over the lazy dog.
{{red}}The quick {{lighten 25}}brown fox{{red}} jumped over the lazy dog.
```

![](http://www.torilmud.com/images/colors/colors_cmd_lighten.png)
![](http://www.torilmud.com/images/colors/colors_cmd_lighten2.png)

### Darken

Darken the color by a percentage. If the color is omitted, it will use the last used color instead.

**Syntax**:

`{{darken [color1] [x]}}`

**Example**
```
{{darken pink 50}}The quick brown fox jumped over the lazy dog.
{{pink}}The quick {{darken pink 50}}brown fox{{pink}} jumped over the lazy dog.
```

![](http://www.torilmud.com/images/colors/colors_cmd_darken.png)
![](http://www.torilmud.com/images/colors/colors_cmd_darken2.png)

### Alternating text

Alternates between two colors every *x* characters.

**Syntax**:

`{{alt [color1] [color2] [x]}}`

**Example**
```
{{alt seagreen forestgreen 3}}The quick brown fox jumped over the lazy dog.{{/alt}}
{{alt red goldenrod}}The quick brown fox jumped over the lazy dog.{{/alt}}
```

![](http://www.torilmud.com/images/colors/colors_cmd_alt.png)
![](http://www.torilmud.com/images/colors/colors_cmd_alt2.png)

### Linear gradient

Creates a linear gradient from color1 to color2 through the length of the enclosed text.

**Syntax**

`{{gradient [color1] [color2]}}`

**Example**
```
{{gradient blue red}}The quick brown fox jumped over the lazy dog.{{/gradient}}
```
![](http://www.torilmud.com/images/colors/colors_cmd_linear_gradient.png)

### Shade gradient

Creates a gradient by gradually mixing it with black and then back again. By default, it will shade
each character by 10%, and approach 95% of the way to all black. Both of these values can be adjusted
by changing `step` and `max`.

**Syntax**

`{{gradient-shade [color] [step] [max]}}`

**Example**
```
{{gradient-shade violet}}The quick brown fox jumped over the lazy dog.
{{gradient-shade violet 25 70}}The quick brown fox jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_cmd_shade_gradient.png)
![](http://www.torilmud.com/images/colors/colors_cmd_shade_gradient2.png)

### Tint gradient

Creates a gradient by gradually mixing it with white and then back again. By default, it will tint
each character by 10%, and approach 95% of the way to all white. Both of these values can be adjusted
by changing `step` and `max`.

**Syntax**

`{{gradient-tint [color] [step] [max]}}`

**Example**
```
{{gradient-tint goldenrod}}The quick brown fox jumped over the lazy dog.
{{gradient-tint goldenrod 5 50}}The quick brown fox jumped over the lazy dog.
 ```
![](http://www.torilmud.com/images/colors/colors_cmd_tint_gradient.png)
![](http://www.torilmud.com/images/colors/colors_cmd_tint_gradient2.png)

### Tone gradient

Creates a gradient by gradually mixing it with grey and then back again. By default, it will add tone to
each character by 10%, and approach 80% of the way to all grey. Both of these values can be adjusted
by changing `step` and `max`.

**Syntax**

`{{gradient-tone [color] [step] [max]}}`

**Example**
```
{{gradient-tone darkgreen}}The quick brown fox jumped over the lazy dog.
{{gradient-tone darkgreen 5 50}}The quick brown fox jumped over the lazy dog.
```

![](http://www.torilmud.com/images/colors/colors_cmd_tone_gradient.png)
![](http://www.torilmud.com/images/colors/colors_cmd_tone_gradient2.png)

### Saturate gradient

Creates a gradient by gradually saturating it and then reversing the saturation. By default, it will saturate
each character by 10%, and go all the way to 100% saturation. Both of these values can be adjusted by changing `step` and `max`.

**Syntax**

`{{gradient-saturate [color] [step] [max]}}`

**Example**
```
 {{gradient-saturate pink}}The quick brown fox jumped over the lazy dog.
 {{gradient-saturate pink 5 50}}The quick brown fox jumped over the lazy dog.
```

![](http://www.torilmud.com/images/colors/colors_cmd_saturate_gradient.png)
![](http://www.torilmud.com/images/colors/colors_cmd_saturate_gradient2.png)

#### Desaturate gradient

Creates a gradient by gradually desaturating it and then reversing the saturation. By default, it will desaturate
each character by 10%, and go all the way to 100% desaturation. Both of these values can be adjusted by changing `step` and `max`.
This works best on lighter colors that have some range for desaturation.

**Syntax**

`{{gradient-desaturate [color] [step] [max]}}`

**Example**
```
{{gradient-desaturate lime}}The quick brown fox jumped over the lazy dog.
{{gradient-desaturate lime 5 50}}The quick brown fox jumped over the lazy dog.
```

![](http://www.torilmud.com/images/colors/colors_cmd_desaturate_gradient.png)
![](http://www.torilmud.com/images/colors/colors_cmd_desaturate_gradient2.png)

## Functions

Color functions are used to change a color programmatically. They can be used anywhere you would use a color, and
really show their usefulness when combined with palettes and variables. Functions change take multiple parameters, separated
by commas.

### Lighten function

Lighten the given color by a percentage.

**Syntax**

`lighten([color], [pct])`

**Example**
```
 {{base red}}The quick {{lighten(red, 25)}}brown fox{{/}} jumped over the lazy dog.
 ```

![](http://www.torilmud.com/images/colors/colors_fn_lighten.png)

### Darken function

Darken the given color by a percentage.

**Syntax**

`darken([color], [pct])`

**Example**
```
{{base coral}}The quick {{darken(coral, 25)}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_fn_darken.png)

### Saturate function

Saturate the given color by a percentage.

**Syntax**

`saturate([color], [pct])`

**Example**
```
{{base grey}}The quick {{saturate(grey, 25)}}brown fox{{/}} jumped over the lazy dog.
```

![](http://www.torilmud.com/images/colors/colors_fn_saturate.png)

### Desaturate function

Desaturate the given color by a percentage.

**Syntax**

`desaturate([color], [pct])`

**Example**
```
{{base blue}}The quick {{desaturate(blue, 25)}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_fn_desaturate.png)

### Hue function

Adjust the hue of the given color. This basically spins the color wheel in a
HSV color space. Take a look at https://en.wikipedia.org/wiki/HSL_and_HSV for
more detail.

**Syntax**

`hue([color], [x])`

**Example**
```
The quick {{hue(yellow, 90)}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_fn_hue.png)

### Shade function

Mix the color with black to create a darker shade.

**Syntax**

`shade([color], [pct])`

**Example**
```
{{base green}}The quick {{shade(green, 75)}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_fn_shade.png)

### Tint function

Mix the color with white to create a lighter tint.

**Syntax**

`tint([color], [pct])`

**Example**
```
{{base green}}The quick {{tint(green, 50)}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_fn_tint.png)
### Tone function

Mix the color with grey to create a tone.

**Syntax**

`tone([color], [pct])`

**Example**
```
{{base green}}The quick {{tone(green, 50)}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_fn_tone.png)

### Complement function

Find a complementing color by spinning the color wheel 180 degrees. This could also be
accomplished with `hue(color, 180)`, but it's easier to tell what the intent is with this.

**Syntax**

`complement([color])`

**Example**
```
{{base wheat}}The quick {{complement(wheat)}}brown fox{{/}} jumped over the lazy dog.
```
![](http://www.torilmud.com/images/colors/colors_fn_complement.png)

# Palettes

Palettes allow you to design a custom color scheme in a `.zon` file, and then refer to those
colors as variables in a text string. This makes it very easy to change colors throughout
an entire zone.

#### .zon syntax

Add a palette section to a `.zon` file at the top, just below the numbers and above the
zon commands.

```
#0
> filename: god_rooms.zon~
God Rooms~
99 0 0 16
1 8 50
1 0 0 0
0 0 0 0
0 0 0 0
1 0 0 0
6 0 0 0
!! Palette
  $base = #6699cc
  $main = #6699cc
  $highlight = slateblue
!! Palette
O 0 59024 99 38		* Beer taps! o_o
O 0 59023 99 38		* Beer taps! o_o
O 0 59022 99 38		* Beer taps! o_o
O 0 59021 99 38		* Beer taps! o_o
*
```

A palette is defined as a collection of variables assigned to either a color name or a hex code. Put one pair on each line, just like above.

#### Usage

Once you have a palette defined, you can use the variables in any string of text to access those colors.

```
The quick {{$main}}brown fox{{/}} jumped over the {{$highlight}}lazy{{/}} dog.
```

You can use the color variables in functions and commands:

```
{{gradient $main darken($highlight, 25)}}The quick brown fox jumped over the lazy dog.

```

#### $base

If you define a palette variable named `$base`, that color will then automatically be used as the base color for
everything in your zone. That means that normalizing a color string will now revert to your zone-wide base color,
rather than plain white.
