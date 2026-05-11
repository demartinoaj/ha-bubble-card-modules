# ha-bubble-card-modules

Collection of style modules for use with [Bubble Card](https://github.com/Clooos/bubble-card).


## Adaptive Lighting Temp Sync
Sets the colors of all light entities displayed with bubble card to the current color of a [adaptive lighting](https://github.com/basnijholt/adaptive-lighting) switch. This allows the cards to change colors to match the real light state as the day goes on. This modules forces all light enties to be dispalyed in this singular color, because I thought it looked nicer then having each light refect it's own true color.

<p float="left">
  <img alt="image" src="https://github.com/user-attachments/assets/7d736a38-e04a-4dc4-9535-be55276d42ce"  width="48%" />
  &nbsp;&nbsp;&nbsp;
  <img alt="image" src="https://github.com/user-attachments/assets/acf755fa-d862-4671-82ff-17eef6de1a61"  width="48%" />
</p>


Note: Requires template sensor sensor.adaptive_lighting_current_rgb_color to function, which should be defined as follows:

```
- unique_id: adaptive_lighting_current_rgb_color 
  name: "Adaptive Lighting Current RGB Color"
  state: >
      {# Get the RGB attribute from the adaptive lighting switch #}
      {% set rgb = state_attr('switch.your_switch_name', 'rgb_color') %}
      {% if rgb is not none %}
      {{ rgb|join(',') }}
      {% else %}
      254,166,87
      {% endif %}
```
