# React Calendar Heatmap

A calendar heatmap component built on SVG, inspired by github's commit calendar graph. The component expands to size of container and is super configurable. [**Try it out on CodeSandbox**](https://codesandbox.io/s/73mk9wlyx).

[![npm version](https://badge.fury.io/js/react-calendar-heatmap.svg)](https://badge.fury.io/js/react-calendar-heatmap)
[![Build Status](https://travis-ci.org/patientslikeme/react-calendar-heatmap.svg?branch=master)](https://travis-ci.org/patientslikeme/react-calendar-heatmap)

[![react-calendar-heatmap screenshot](/assets/react-calendar-heatmap.png?raw=true)](http://patientslikeme.github.io/react-calendar-heatmap/)

## Setup

Install the npm module with yarn or npm:

```bash
yarn add react-calendar-heatmap
```

## Usage

Import the component:

```javascript
import CalendarHeatmap from 'react-calendar-heatmap';
```

Import styles. You can directly import from the module, which requires a CSS loader (set up by default in create-react-app):

```javascript
import 'react-calendar-heatmap/dist/styles.css';
```

If you don't have a CSS loader, you can simply [copy the stylesheet](src/styles.css) into a file in your project and import it instead.

To show a basic heatmap from January 1st to April 1st:

```javascript
<CalendarHeatmap
  startDate={new Date('2016-01-01')}
  endDate={new Date('2016-04-01')}
  values={[
    { date: '2016-01-01' },
    { date: '2016-01-22' },
    { date: '2016-01-30' },
    // ...and so on
  ]}
/>
```

## Configuring colors

To use the color scale shown in the [live demo](http://patientslikeme.github.io/react-calendar-heatmap/) based on the github contribution graph, you can set the `classForValue` prop, a function that determines which CSS class to apply to each value:

```javascript
<CalendarHeatmap
  values={[
    { date: '2016-01-01', count: 1 },
    { date: '2016-01-03', count: 4 },
    { date: '2016-01-06', count: 2 },
    // ...and so on
  ]}
  classForValue={(value) => {
    if (!value) {
      return 'color-empty';
    }
    return `color-scale-${value.count}`;
  }}
/>
```

Then you use CSS to set colors for each class:

```css
.react-calendar-heatmap .color-scale-1 { fill: #d6e685; }
.react-calendar-heatmap .color-scale-2 { fill: #8cc665; }
.react-calendar-heatmap .color-scale-3 { fill: #44a340; }
.react-calendar-heatmap .color-scale-4 { fill: #1e6823; }
```

## Other configuration

See full configuration options on the [live demo page](http://patientslikeme.github.io/react-calendar-heatmap/).

## Contributing

Take a look at [CONTRIBUTING.md](/CONTRIBUTING.md) to see how to develop on react-calendar-heatmap.

## License

react-calendar-heatmap is Copyright &copy; 2016 PatientsLikeMe, Inc. and is released under an MIT License.  See COPYING for details.
