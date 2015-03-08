# mod-elevator-panel

HTML UI element that resembles an elevator panel with an "up" button, "down" button and a display.
Implemented as a web component using [Google Polymer](https://www.polymer-project.org).

### Features

 * Increase, decrease numeric value between min and max value
 * Change event consolidates multiple changes into one event
 * Click/touch and hold changes values continously (the longer the faster the value changes)
 * Vertical or horizontal layout
 * Map values to arbitrary strings for non-numeric presentation
 * Most parameters and styles customizable

### Dependencies

 * polymer#^0.5.5
 * webcomponentsjs#^0.5.5"
 * core-icon#^0.5.5
 * core-icons#^0.5.5

### Demo

[Elevator panel examples](http://oliverdm.github.io/mod-elevator-panel/demo.html)

### Example Usage

```
<link rel="import" href="app-elevator-panel.html">

<mod-elevator-panel id="panel"
                    min="0"
                    max="100"
                    value="50"
                    increment="5"
                    valueMap="{{ {0: 'Min', 100: 'Max'} }}"
                    valuePrefix=""
                    valueSuffix="%"
                    iconMore="add-circle"
                    iconMore="remove-circle"
                    eventDelay="1000"
                    holdInterval="250"
                    horizontal></mod-elevator-panel>
```

### Styling

Icon style in neutral state:
```
#panel::shadow core-icon {
  width: 48px;
  height: 48px;
  color: black;
  background-color: transparent;
}
```

Icon style in disabled state:
```
#panel::shadow core-icon[disabled] {
  color: lightgray !important;
  background-color: transparent !important;
}
```

Icon style when hovering with mouse:
```
#panel::shadow core-icon:hover {
  color: white;
  background-color: turquoise;
}
```

Icon style in active state:
```
#panel::shadow core-icon:active {
  color: turquoise;
  background-color: transparent;
}
```

Value style:
```
#panel::shadow #valueContainer {
  font-size: 1.5em;
  font-weight: lighter;
}
```

### <mod-elevator-panel> API

More documentation available in the source code.

##### `change` (event)

Fired when the value changed.
Can represent multiple changes made in quick succession.

##### `mappedValue` (read-only attribute)

Returns the mapped value or null if no mapping exists for the current value.

##### `disabled` (attribute)

Enables or disables the control.

##### `horizontal` (property)

Switches to horizontal layout.

##### `valuePrefix` (property)

Prefix that is prepended to the value.

##### `valueSuffix` (property)

Prefix that is appended to the value.

##### `iconMore` (property)

The icon name as supplied to `<core-icon icon="...">`.
Alternatively an object with two keys to change the icon depending on the layout: `{ "v": "verticalIcon", "h": "horizontalIcon" }`.
The latter is only needed if the layout can change dynamically.

##### `iconLess` (property)

Same as `iconMore` but for the decrement button.

##### `value` (property)

The current (and initial) value.

##### `min` (property)

The minimum value.

##### `max` (property)

The maximum value.

##### `increment` (property)

The value that is added or subtracted during each change.

##### `valueMap` (property)

An object that maps values to arbitrary strings for presentation purposes. (object, array, or JSON string)

##### `eventDelay` (property)

The pause in user input required for the `change` event to trigger (in milliseconds).

##### `holdInterval` (property)

The frequency with which the value is changed when holding down the mouse/touching (in milliseconds).