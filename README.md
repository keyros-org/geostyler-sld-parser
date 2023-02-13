# geostyler-sld-parser

[![Test Push to Master](https://github.com/geostyler/geostyler-sld-parser/actions/workflows/on-push-master.yml/badge.svg)](https://github.com/geostyler/geostyler-sld-parser/actions/workflows/on-push-master.yml)
[![Coverage Status](https://coveralls.io/repos/github/terrestris/geostyler-sld-parser/badge.svg?branch=master)](https://coveralls.io/github/terrestris/geostyler-sld-parser?branch=master)
[![npm version](https://badge.fury.io/js/geostyler-sld-parser.svg)](https://www.npmjs.com/package/geostyler-sld-parser)

[GeoStyler](https://github.com/terrestris/geostyler/) Style Parser implementation for Styled Layer Descriptor (SLD)

### How to use

ES6:
```js
import SLDParser from 'geostyler-sld-parser';
import { Style } from 'geostyler-style';

const pointSimplePoint = {
  name: 'My Style',
  rules: [
    {
      name: 'My Rule',
      symbolizers: [
        {
          kind: 'Mark',
          wellKnownName: 'circle',
          color: '#FF0000',
          radius: 6
        }
      ]
    }
  ]
};

const parser = new SLDParser();

parser
  .writeStyle(pointSimplePoint)
  .then(({output: sld}) => console.log(sld))
  .catch(error => console.log(error));


// Read style from string
let sldString = '<?xml version="1.0" encoding="UTF-8"?><sld:StyledLayerDescriptor xmlns="http://www.opengis.net/sld" xmlns:sld="http://www.opengis.net/sld" xmlns:gml="http://www.opengis.net/gml" xmlns:ogc="http://www.opengis.net/ogc" version="1.0.0"> <sld:NamedLayer> <sld:Name>Default Styler</sld:Name> <sld:UserStyle> <sld:Name>Default Styler</sld:Name> <sld:Title>Gravel_Program_2016</sld:Title> <sld:FeatureTypeStyle> <sld:Name>name</sld:Name> <sld:Rule> <sld:MinScaleDenominator>1.0</sld:MinScaleDenominator> <sld:MaxScaleDenominator>1.0E7</sld:MaxScaleDenominator> <sld:LineSymbolizer> <sld:Stroke> <sld:CssParameter name="stroke">#8000FF</sld:CssParameter> <sld:CssParameter name="stroke-width">3.000</sld:CssParameter> </sld:Stroke> </sld:LineSymbolizer> </sld:Rule> </sld:FeatureTypeStyle> </sld:UserStyle> </sld:NamedLayer> </sld:StyledLayerDescriptor>';

parser
  .readStyle(sldString)
  .then(({output: sldObject}) => console.log(sldObject))
  .catch(error => console.log(error));

```

Browser:

```js
const pointSimplePoint = {
  name: "My Style",
  rules: [
    {
      name: "My Rule",
      symbolizers: [
        {
          kind: "Mark",
          wellKnownName: "Circle",
          color: "#FF0000",
          radius: 6
        }
      ]
    }
  ]
};
var parser = new GeoStylerSLDParser.SldStyleParser();
parser
  .writeStyle(pointSimplePoint)
  .then(({output: sld}) => console.log(sld))
  .catch(error => console.log(error));
    
// Read style from string
var sldString = '<?xml version="1.0" encoding="UTF-8"?><sld:StyledLayerDescriptor xmlns="http://www.opengis.net/sld" xmlns:sld="http://www.opengis.net/sld" xmlns:gml="http://www.opengis.net/gml" xmlns:ogc="http://www.opengis.net/ogc" version="1.0.0"> <sld:NamedLayer> <sld:Name>Default Styler</sld:Name> <sld:UserStyle> <sld:Name>Default Styler</sld:Name> <sld:Title>Gravel_Program_2016</sld:Title> <sld:FeatureTypeStyle> <sld:Name>name</sld:Name> <sld:Rule> <sld:MinScaleDenominator>1.0</sld:MinScaleDenominator> <sld:MaxScaleDenominator>1.0E7</sld:MaxScaleDenominator> <sld:LineSymbolizer> <sld:Stroke> <sld:CssParameter name="stroke">#8000FF</sld:CssParameter> <sld:CssParameter name="stroke-width">3.000</sld:CssParameter> </sld:Stroke> </sld:LineSymbolizer> </sld:Rule> </sld:FeatureTypeStyle> </sld:UserStyle> </sld:NamedLayer> </sld:StyledLayerDescriptor>';


parser
  .readStyle(sldString)
  .then(({output: sldObject}) => console.log(sldObject))
  .catch(error => console.log(error));
```
