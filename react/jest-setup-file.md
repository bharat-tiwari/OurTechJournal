# Jest setup file

Sometimes we may want to add some default mocked API or module to our unit tests or to extend the JSDOM that jest uses. These mocked APIs/Modules/extended DOM can be defined in a jest setup file. 

If we want Jest to use this setup file when running our unit-tests, we need to specify the setup file name in jest config \(in package.json, or on command script, or in the jest.config.js\)

If we are using CRA-based react project, no need to specify jest setup file name in package.json. Just [create a `setupTests.js` file under `src`](https://github.com/jsdom/jsdom/issues/2155#issuecomment-366703395) folder and CRA will automatically see and use it for jest configuration.



e.g. [below](https://github.com/jsdom/jsdom/issues/2155#issuecomment-366703395) 👇

```text
window.HTMLMediaElement.prototype.load = () => { /* do nothing */ };
window.HTMLMediaElement.prototype.play = () => { /* do nothing */ };
window.HTMLMediaElement.prototype.pause = () => { /* do nothing */ };
window.HTMLMediaElement.prototype.addTextTrack = () => { /* do nothing */ };
```

An example of jest setup for React-native

```text
import { NativeModules as RNNativeModules } from "react-native";

const mockUIManager = {
  RCTView: () => ({
    directEventTypes: {}
  })
};

RNNativeModules.UIManager = RNNativeModules.UIManager || mockUIManager;
// RNNativeModules.UIManager.RCTView = RNNativeModules.UIManager.RCTView || {};
RNNativeModules.RNGestureHandlerModule = RNNativeModules.RNGestureHandlerModule || {
  State: { BEGAN: "BEGAN", FAILED: "FAILED", ACTIVE: "ACTIVE", END: "END" },
  attachGestureHandler: jest.fn(),
  createGestureHandler: jest.fn(),
  dropGestureHandler: jest.fn(),
  updateGestureHandler: jest.fn(),
  Directions: {}
};
RNNativeModules.PlatformConstants = RNNativeModules.PlatformConstants || {
  forceTouchAvailable: false
};
RNNativeModules.KeyboardObserver = RNNativeModules.KeyboardObserver || {};

jest.mock("NativeAnimatedHelper");

jest.mock("TextInput", () => {
  const RealComponent = require.requireActual("TextInput");
  const React = require("React");

  class TextInput extends React.Component {
    render() {
      return React.createElement(
        "TextInput",
        { ...this.props, autoFocus: false, blur: false },
        this.props.children
      );
    }
  }
  TextInput.propTypes = RealComponent.propTypes;
  return TextInput;
});

// mock DatePicker component from Native-base
jest.mock("DatePickerIOS", () => {
  const RealComponent = require.requireActual("DatePickerIOS");
  const React = require("React");

  class DatePickerIOS extends React.Component {
    render() {
      return React.createElement(
        "DatePickerIOS",
        { ...this.props, setNativeProps: false },
        this.props.children
      );
    }
  }
  DatePickerIOS.propTypes = RealComponent.propTypes;
  return DatePickerIOS;
});
```

And **jest.config.js** \(required only for non-CRA based react/react-native projects\) 👇

\( For CRA/CRNA projects, we cann't customize jest config using a separate jest.config.js to specify a jest setup file. CRA/CRNA looks for `src/setupTests.js`, and if found one, uses it for jest setup. \)  

```text
module.exports = {
  transform: {
    "^.+\\.jsx?$": "<rootDir>/node_modules/babel-jest",
    "^.+\\.tsx?$": "ts-jest"
  },
  transformIgnorePatterns: [
    "node_modules/(?!react-native|native-base|react-native-vector-icons|react-navigation|@react-navigation|native-base-shoutem-theme|@shoutem/theme|@shoutem/animation|@shoutem/ui|tcomb-form-native)"
  ],
  preset: "react-native",
  moduleNameMapper: {
    "^@/(.*)$": "<rootDir>/src/$1"
  },
  testRegex: "(/__tests__/.*|/src/.*\\.(test|spec))\\.(tsx?)$",
  moduleFileExtensions: [
    "ts",
    "tsx",
    "js",
    "jsx",
    "json",
    "ios.ts",
    "ios.tsx",
    "android.ts",
    "android.tsx"
  ],
  collectCoverage: true,
  collectCoverageFrom: [
    "src/**/*.js",
    "src/**/*.jsx",
    "src/**/*.ts",
    "src/**/*.tsx",
    "!src/**/index.ts",
    "!src/**/styles.ts",
    "!<rootDir>/node_modules/",
    "!<rootDir>/index.js",
    "!<rootDir>/jest.setup.js",
    "!build/**/*.*"
  ],
  setupFiles: ["./jest.setup.js"],
  setupFilesAfterEnv: ["./setup-tests.js"]
};
```

