---
---
title: custom_card_nwootton_moon_phase
hide:
  - toc
---
<!-- markdownlint-disable MD046 -->

# Custom-card "ISP Status"

The `custom_card_nwootton_moon_phase` allows you to display a simple translation of the moon phases in the local language.

Includes translations for DE and ES, but don't shoot the messenger, I used Google Translate, so feel free to correct.

## Credits

Author: nwootton - 2022
Version: 0.0.1

Code is based on the `card_generic` that comes with UI-Minimalist platform theme.
## Changelog

<details>
<summary>0.0.1</summary>
Initial release
</details>


## Usage

```yaml
  - type: 'custom:button-card'
    template: custom_card_nwootton_moon_phase
    entity: sensor.moon
```


## Requirements

Requires the Moon integration to be installed

## Variables

<table>
<tr>
<th>Variable</th>
<th>Example</th>
<th>Required</th>
<th>Explanation</th>
</tr>
<tr>
<td>entity_</td>
<td>sensor.moon</td>
<td>yes</td>
<td>Moon phase</td>
</tr>
</table>

## Template code

```yaml
---
custom_card_nwootton_moon_phase:
  template:
    - "icon_info_bg"
    - "ulm_language_variables"
    - "custom_card_nwootton_moon_phase_language_variables"
  name:  >
    [[[
      var myName = "";

      if ( entity.state == 'new_moon') {
        myName = variables.custom_card_nwootton_moon_phase_new_moon;
      } else if ( entity.state == 'waxing_crescent') {
        myName = variables.custom_card_nwootton_moon_phase_waxing_crescent;
      } else if ( entity.state == 'full_moon') {
        myName = variables.custom_card_nwootton_moon_phase_full_moon;
      } else if ( entity.state == 'waning_crescent') {
        myName = variables.custom_card_nwootton_moon_phase_waning_crescent;
      } else {
        myName = entity.state;
      }
      return myName;
    ]]]
  label: >
    [[[ return entity.attributes.friendly_name]]]


```