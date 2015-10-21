# react-native-file-upload  [![NPM version](https://img.shields.io/npm/v/react-native-file-upload.svg?style=flat-square)](https://www.npmjs.com/package/react-native-file-upload)

A file upload plugin for react-native written by Objective-C.

* Support to upload multiple files at a time
* Support to files and fields

## Getting started

1. `npm install react-native-file-upload --save`
2. In XCode, in the project navigator, right click `your project` ➜ `Add Files to [your project's name]`
3. Go to `node_modules` ➜ `react-native-file-upload` and add `FileUpload.m`
4. Run your project (`Cmd+R`)

## Usage

All you need is to export module `var FileUpload = require('NativeModules').FileUpload;` and direct invoke `FileUpload.upload`.

```javascript
'use strict';

var React = require('react-native');
var FileUpload = require('NativeModules').FileUpload;

var {
  AppRegistry,
  StyleSheet,
  Text,
  View,
} = React;

var FileUploadDemo = React.createClass({
  componentDidMount: function() {
    var obj = {
        uploadUrl: 'http://127.0.0.1:3000',
        method: 'POST', // default 'POST',support 'POST' and 'PUT'
        headers: {
          'Accept': 'application/json',
        },
        fields: {
            'hello': 'world',
        },
        files: [
          {
            name: 'one', // optional, if none then `filename` is used instead
            filename: 'one.w4a', // require, file name
            filepath: '/xxx/one.w4a', // require, file absoluete path
            filetype: 'audio/x-m4a', // options, if none, will get mimetype from `filepath` extension
          },
        ]
    };
    FileUpload.upload(obj, function(err, result) {
      console.log('upload:', err, result);
    })
  },
  render: function() {
    return (
      <View style={styles.container}>
        <Text style={styles.welcome}>
          Welcome to React Native!
        </Text>
      </View>
    );
  }
});

var styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
});

AppRegistry.registerComponent('FileUploadDemo', () => FileUploadDemo);
```

## License

MIT
