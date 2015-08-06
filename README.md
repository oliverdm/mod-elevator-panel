# odm-elevator-panel

HTML UI element that resembles an elevator panel with an "up" button, "down" button and a display.
Implemented as a web component for [Google Polymer 1.0](https://www.polymer-project.org).

### Features

 * Increase, decrease numeric value between min and max value
 * Change event triggered
 * Vertical or horizontal layout
 * Custom CSS mixins
 * Optional mapping of numeric values to strings

### Demo & Examples

[Examples](http://oliverdm.github.io/odm-elevator-panel/demo.html)

Element with all attributes defined:

```
<link rel="import" href="odm-elevator-panel.html">

<odm-elevator-panel id="panel"
                    min="0"
                    max="100"
                    value="50"
                    increment="5"
                    value-map='{"0": "Min", "100": "Max"}'
                    value-prefix="+"
                    value-suffix="%"
                    icon-more-vertical="add-circle"
                    icon-more-horizontal="add-circle"
                    icon-less-vertical="remove-circle"
                    icon-less-horizontal="remove-circle"
                    event-delay="500"
                    hold-interval="200"
                    horizontal
                    disabled></odm-elevator-panel>
```

### Custom Styles

Custom styles possible via [Custom CSS mixins](https://www.polymer-project.org/1.0/docs/devguide/styling.html#custom-css-mixins).

Example:

```
#mypanel {
    --odm-elevator-panel-icon: {
        color: black;
        background-color: transparent;
    };
}
```

Property                           | Description
---------------------------------- | ----------------------------------------
--odm-elevator-panel-icon          | Styles both icon buttons in normal state
--odm-elevator-panel-icon-disabled | Styles both icon buttons in disabled state
--odm-elevator-panel-icon-hover    | Styles both icon buttons when hovering
--odm-elevator-panel-icon-active   | Styles both icon buttons when active
--odm-elevator-panel-value         | Styles the displayed value


### <odm-elevator-panel> API

All properties are also available as attributes of the element when the name is converted (camelCase to dash, e.g. `valuePrefix -> value-prefix`).
However, only changes to the `disabled` and `horizontal` properties are reflected back to HTML.

More documentation available in the source code.

##### `change` (event)

Fired when the value changed.
When multiply changes are made in quick succession, only the last change causes an event to be fired (according to `eventDelay` property).

##### `setMapping(map)` (function)

Programmatically set how values are mapped for presentation. 
Valid values are: Object, Array, Null or Function.

##### `disabled` (property)

Enables or disables the control.
Reflected back to HTML.

##### `horizontal` (property)

Switches to horizontal layout.
Reflected back to HTML.

##### `valuePrefix` (property)

Prefix that is prepended to the value.

##### `valueSuffix` (property)

Prefix that is appended to the value.

##### `iconMoreVertical`, `iconMoreHorizontal`, `iconLessVertical`, `iconLessHorizontal` (properties)

The icon name as supplied to `<iron-icon icon="...">`.

##### `value` (property)

The current (and initial) value.

##### `min` (property)

The minimum value.

##### `max` (property)

The maximum value.

##### `increment` (property)

The value that is added or subtracted during each change.

##### `valueMap` (property)

An object or array as JSON formatted string that maps values to arbitrary strings for presentation.

##### `eventDelay` (property)

The pause in user input required for the `change` event to trigger (in milliseconds).

##### `holdInterval` (property)

The frequency with which the value is changed when holding down the mouse/touching (in milliseconds).