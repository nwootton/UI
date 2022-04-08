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
custom_card_nwootton_isp_status:
  template:
    - "icon_info_bg"
    - "ulm_language_variables"
    - "custom_card_nwootton_isp_status_language_variables"
  label:  >
    [[[
      var myName = "";

      if ( entity.state == 'online') {
        myName = variables.custom_card_nwootton_isp_status_online;
      } else if ( entity.state == 'offline') {
        myName = variables.custom_card_nwootton_isp_status_offline;
      } else {
        myName = entity.state;
      }

      return myName;
    ]]]
  name: >
    [[[ return entity.attributes.friendly_name]]]
  icon: |
    [[[
      if (entity.state == 'online') {
        return 'mdi:lan-connect';
      } else if (entity.state == 'offline') {
        return 'mdi:lan-disconnect';
      } else {
        return 'mdi:lan-pending';
      }
    ]]]
  styles:
    icon:
      - color: "rgba(var(--color-theme),0.9)"
    label:
      - justify-self: "start"
      - align-self: "start"
      - font-weight: "bolder"
      - font-size: "12px"
      - filter: "opacity(40%)"
      - margin-left: "12px"
    name:
      - align-self: "end"
      - justify-self: "start"
      - font-weight: "bold"
      - font-size: "14px"
      - margin-left: "12px"
      - filter: "opacity(100%)"
    grid:
      - grid-template-areas: "'i n' 'i l'"
      - grid-template-columns: "min-content auto"
      - grid-template-rows: "min-content min-content"
  state:
    - operator: template
      value: >
        [[[
          return entity.state == 'online';
        ]]]
      styles:
        icon:
          - color: 'rgba(var(--color-green),1)'
        img_cell:
          - background-color: 'rgba(var(--color-green),0.2)'

    - operator: template
      value: >
        [[[
          return entity.state == 'offline';
        ]]]
      styles:
        icon:
          - color: 'rgba(var(--color-red),1)'
        img_cell:
          - background-color: 'rgba(var(--color-red),0.2)'


```