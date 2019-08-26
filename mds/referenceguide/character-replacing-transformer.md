---
id: character-replacing-transformer
title: Character replacing transformer
sidebar_label: Character replacing transformer
---
#### Transformer that replaces certain Unicode code points in the (string) payload.
Transformer that replaces certain Unicode code points in the (string) payload.

Note that this is not meant to fix issues caused by using an incorrect character set when reading data, but for replacing unwanted Unicode code points (such as control characters) in a text.

#### Targets
The target characters that need to be replaced. Characters must be entered using the hexidecimal notation for Unicode code points, i.e. in the range <code>U+0000</code> to <code>U+10FFFF</code>. See <a href="https://en.wikipedia.org/wiki/List_of_Unicode_characters" target="_blank">here</a> for a list of Unicode characters.

You can specify multiple characters by using a comma separated list, and ranges by using the minus sign. For example <code>U+0000-U+001F, U+007F, U+0080-U+009F</code> matches all C0 and C1 control codes plus the delete character.

An empty value for this setting is valid, but it will not match any characters.

#### Replacement
The (single) character that will replace any of the specified target characters in the output. Characters must be entered using the hexidecimal notation for Unicode code points, i.e. in the range <code>U+0000</code> to <code>U+10FFFF</code>. See <a href="https://en.wikipedia.org/wiki/List_of_Unicode_characters" target="_blank">here</a> for a list of Unicode characters.

An empty value for this setting will result in all target characters to be replaced by nothing, basically deleting them. Note that when replacing characters in a "fixed width" format this is usually unwanted: in these cases you'd normally want to use a padding character like <code>U+0020</code> (space) as the replacement.

#### Inverse match
Normally this transformer will replace all the listed target characters with the replacement. Using an inverse match will result in all characters <b>except</b> the ones listed to be replaced with the replacement. This can be useful to guarantee that only a limited subset of all Unicode code points can be present in the output.

Default is <code>false</code>.

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

