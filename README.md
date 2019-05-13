# PLAR-Portfolio
Housing Documents for PLAR

# IEGBBR Mobile App Documentation

Last updated: May 03, 2019

## Table of Contents

- [Quick start](#quick-start)
- [Directory Structure](#directory-structure)
- [Dependencies](#dependencies)
- [MET](#met)
- [Styles](#styles)
  - [Stylesheets](#stylesheets)
- [Scripting](#scripting)
  - [Script files](#script-files)
  - [Data files](#data-files)
- [Testing](#testing)
  - [Testing file structure](#testing-file-structure)
- [Multilingualism](#multilingualism)
- [Updating the app](#updating-the-app)
  - [Updating phonegap plugins](#updating-phonegap-plugins)
  - [Updating dependencies](#updating-dependencies)
  - [Adding new views](#adding-new-views)
  - [Adding new IEGBBR content](#adding-new-iegbbr-content)
  - [Adding new state property to the application store](#adding-new-state-property-to-the-application-store)

## Quick start

Requires Node >= 8.X.X

- Install dependencies  `npm install`
- Add platforms `cordova platform add {android|ios|browser}`
- Test `npm run test{-watch}`
- Build `npm run build`
- Build prod `npm run prod{-ios|android}`
- Test platform `npm run {android|ios|browser}`
- Run locally `npm start`

## Directory Structure

| Directory (www) | Info |
| ------------- | ------------- |
| / | Project root |
| /.circleci | CircleCI configuration |
| /Documentation | Documentation |
| /platforms | Cordova platforms directory |
| /plugins | Cordova plugins directory |
| /src | Source code and resources |
| /src/res | Phonegap/Cordova resources |
| /src/met | MET subdirectory |
| /src/components | Components |
| /src/components/_tests | Component test files |
| /src/components/data | Component data |
| /src/css | Styling resources |
| /src/css/bootstrap | Bootstrap files (css, fonts, js) |
| /src/css/fonts | Font files |
| /src/data | Data files |
| /src/images | Image files |
| /src/actions | Actions |
| /src/reducers | Reducers |

Other folders are used in the build process

## Dependencies

Requires Node >= 8.X.X

<details>
  <summary>Click to expand</summary>
  <ul>
    <li> <b>met</b>: <i>2.0.0</i></li>
    <ul><li> Health Canada's Mobile Experience Template (MET)</li></ul>
  </ul>
</details>

## MET

This application uses Health Canada's [Mobile Experience Template (MET)](https://github.com/hc-sc/met). This library contains generic components, styles and scripts utilized by all HC mobile applications.

## Styles

The main styling framework is Bootstrap, version 3.3.7, using the [react-bootstrap](https://react-bootstrap.github.io/) library found in MET. All other resources can be found in the 'src/css/' directory or in the .../component/styles directory for individualized component stylesheets. Styles should be written in LESS. All files get transpiled and compressed into 'main.css' by webpack on build.

### Stylesheets

- **bootstrap-theme.css**
  - IEGBBR bootstrap theme
- **iegbbr-ftss-const.less**
  - IEGBBR LESS constants
- **iegbbr-ftss-footnotes.less**
  - IEGBBR footnote styles
- **iegbbr-ftss-mobile.less**
  - Main IEGBBR stylesheet

## Scripting

This application is written primarly using [Javascript XML (JSX)](https://reactjs.org/docs/introducing-jsx.html). JSX is a Javascript syntax extension library. It is almost identical to JS with the advantage of allowing inline tag templating. For more on JSX see the [JSX in depth](https://reactjs.org/docs/jsx-in-depth.html) page of the React documentation.

### Script files

- **src/index.jsx**
  - Application entry point. This file handles initialization of the application as well as local data persistance.
- **src/components/--.jsx**
  - IEGBBR component files. Contains all IEGBBR components.
  - **Main.jsx**
    - Main application container. Renders application body content. Handles routing, transitions and external links. Contains and renders application hamburger menu. 
  - **Landing.jsx**
    - Landing view. Main page of the IEGBBR app; containing the links to the main content.
      - **Part1.jsx**
      - Main content Part 1 view; contains the National Biosafety Biosecurity Regulatory Frameworks in the IEGBBR Member Countries content and tables of the IEGBBR document.
      - **Part2.jsx**
      - Main content Part 2 view; contains the Processes, Procedures, and Record Management Requirements Related to Biosecurity-Biosafety Oversight content and tables of the IEGBBR document.
      - **Part3.jsx**
      - Main content Part 3 view; contains the Risk Assessment Requirements for Regulatory Approval content and tables of the IEGBBR document.
      - **Part4.jsx**
      - Main content Part 4 view; contains the Compliance with Biosecurity-Biosafety Frameworks and Oversight content and tables of the IEGBBR document.
      - **Part5.jsx**
      - Main content Part 5 view; contains the Accountability and Personnel Requirements, Training, Outreach and
  Awareness content and tables of the IEGBBR document.
  - **Executive.jsx**
    - Executive Summary view; contains the Executive Summary section of the IEGBBR document.
  - **Acronyms.jsx**
    - List of Acronyms view; contains the List of Acronyms section of the IEGBBR document.
  - **Preface.jsx**
    - Preface view; contains the Preface section of the IEGBBR document.
  - **Countries.jsx**
    - Country Specific Analysis view; contains the specific analysis for each country within the IEGBBR group, and the corresponding details found within the Country Specific Analysis section of the IEGBBR document.
  - **Agreements.jsx**
    - Agreements, Conventions, & Initiatives view; contains the International Biosafety and Biosecurity Agreements, Conventions, Initiatives, and International Biosafety and Biosecurity Capacity-Building section of the IEGBBR document.
  - **LanguageSelection.jsx**
    - Language selection view
- **src/store.jsx**
  - Contains default method using initial state, history and middleware to generate the application store.
- **src/actions/index.jsx**
  - Contains all redux action constants and logic
- **src/reducers/--Reducer.jsx**
  - Reducer modules used to apply mutations to the state
- **src/reducers/index.jsx**
  - Exports combined reducer from reducer modules
- **src/cordova.js**
  - Dummy script to inject when doing web builds

### Data files

- **src/data/const.js**
  - Exports application constants
- **src/components/data/--.json**
  - Component data files. These contain text content and mappable component data.
- **src/data/--.json**
  - Application data files (IEGBBR, search indicies, constants, etc...)

## Testing

Testing is done using the [karma](https://github.com/karma-runner/karma) runner with the [mocha](https://mochajs.org) testing framework. Testing can be run one time with the `npm run test` command, or the `npm run test-watch` command for contuous monitoring of the project during development.

The [Enzyme](https://github.com/airbnb/enzyme) library is used to mount React components for DOM testing. [Sinon](http://sinonjs.org/) is used to spy on component methods. [Expect](https://facebook.github.io/jest/docs/en/expect.html) is the assertion library used to validate the results.

For more on testing see the testing page in the [MET documentation](https://github.com/hc-sc/met).

### Testing file structure

| Item | Description |
| ------------- | ------------- |
| /karma.conf.js | [Karma configuration file](https://karma-runner.github.io/2.0/config/configuration-file.html) |
| /tests.webpack.js | Test file context |
| /src/reducers/_tests | IEGBBR reducer test files |
| /src/components/_tests| IEGBBR component test files |
| /src/met/components/_tests | MET test files |

## Multilingualism

When a user first opens the application, they are prompted to choose their language.  That value is stored using [Local Storage](https://www.w3schools.com/html/html5_webstorage.asp).

If the user has already selected a language they are immediatly brought to the main options view instead of the language selection view.

At the top level of all component data, the data should be split between English and French, allowing the component to easily access the appropriate text for the selected language.

Example for the JSX and JSON files below:

```jsx
//src/components/data/Landing.jsx

import text from './data/Landing.json'

class Landing {
  ...
  render() {
    return <h1>text[this.props.lang].title</h1>
  }
}

```

```javascript
//src/components/data/Landing.json

{
  "en": {
    "content": "Detailed Information on National Biosafety and Biosecurity Regulatory Oversight in IEGBBR Member Countries",
    "links": {
      "part1": "Part 1: National Biosafety Biosecurity Regulatory Landscape in the IEGBBR Member Countries",
      "part2": "Part 2: Processes, Procedures, and Record Management Requirements Related to Biosecurity-Biosafety Oversight",
      "part3": "Part 3: Risk Assessment Requirements for Regulatory Approval",
      "part4": "Part 4: Compliance with Biosecurity-Biosafety Frameworks and Oversight",
      "part5": "Part 5: Accountability and Personnel Requirements, Training, Outreach and Awareness"
    },

  "fr": {
    "content": "Information détaillée sur la surveillance réglementaire de la biosécurité et de la biosûreté à l’échelle nationale dans les pays membres de l’IEGBBR",
    "links": {
      "part1": "Partie 1 : Les cadres nationaux de réglementation de la biosécurité et de la biosûreté dans les pays membres de l’IEGBBR",
      "part2": "Partie 2 : Processus, procédures et exigences en matière de gestion des dossiers dans le cadre de la surveillance de la biosûreté et de la biosécurité",
      "part3": "Partie 3 : Exigences en matière d’évaluation des risques aux fins de’autorisation réglementaire",
      "part4": "Partie 4 : Conformité aux cadres et à la surveillance de biosûreté et de biosécurité",
      "part5": "Partie 5 : Exigences en matière de reddition de comptes et de personnel, formation, rayonnement et sensibilisation"
    }
  }
}

```

## Updating the app

When changing the app, a new version number should be used to easily identify that the app has changed. This number is located in the `package.json` file and is updated in the app via webpack.

### Updating phonegap plugins

1. Update in `src/config.xml`

### Updating dependencies

1. Update via npm. `npm install {package}@{version}`

### Adding new views

1. Create the component in `src/components`, along with the optional data and test files `src/components/data`. For example: `src/components/data/{name}.json` & `src/components/{name}.jsx`
2. Add routing rules for the new view in `src/components/Main.jsx`

   Example Outlined Below:
   
   ```jsx
      //src/components/main.jsx

        // App Components (located at the top of the file)
        import Landing from './Landing';
        import LanguageSelection from './LanguageSelection';
        import Components from './Components';
        import Intro from './Intro';
        import {Name} from './{Name}'; // Example of where to add the new import
    ```
   
    ```jsx
      // src/components/main.jsx

      ...
        <Switch location={this.props.router.location}>
          <Route key="{name}" exact path="/:lang/{name}" component={Name} /> // Example of adding route
          <Route key="part1" exact path="/:lang/part1" component={Part1} />
          <Route key="part2" exact path="/:lang/part2" component={Part2} />
          <Route key="part3" exact path="/:lang/part3" component={Part3} />
          <Route key="part4" exact path="/:lang/part4" component={Part4} />
          <Route key="part5" exact path="/:lang/part5" component={Part5} />
          <Route key="lang" exact path="/" render={LanguageSelection} />
          <Route key="home" exact path="/:lang/main" component={Landing} />
         ...
        </Switch>
       ...
     ```
3. Update the content within the `src/components/data/Main.json` file under the `"links": {...` portion if the new view is to be accessable via the hamburger menu.

   Example Outlined Below:
   
     ```javascript
          // src/components/data/main.json

        ...
             "links": {
               "{name}": "{Name}",  // Example (Order them according to the document structure)
               "exec": "Executive Summary",
               "acronyms": "List of Acronyms",
               "preface": "Preface",
               "countries": "Country Specific Analysis",
               "agreements": "Agreements, Conventions, & Initiatives",
               "terms": "Terms and Conditions"
              }
    ```

### Adding new IEGBBR content

1. The main content is housed with the `src/components/data/DetailedInfo.json` file.
    - Any new content being added into the core IEGBBR document (Part 1 through 5) is to be added here, following the *IEGBBR Main Content Data Schema.*
    
    Example Outlined Below:
    
    ```javascript
       //src/components/data/DetailedInfo.json

        {
          "en": {
            "countries": [
                {
                  "index": "0",
                  "name": "Canada",
                  "iso": "CA",
                  "tableOne": [
                    {
                      "element": "ul",
                      "child": [
                        {
                          "element": "li",
                          "child": "This is the test content for Canada"
                        },
                        {
                          "element": "li",
                          "child": "This is the test content for Canada"
                        }
                      ]
                    }
                  ],
                  "tableTwo": [
                    {
                      "element": "ul",
                      "child": [
                        {
                          "element": "li",
                          "child": "This is the test content for Canada"
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          }
    ```
    
### Adding new state property to the application store

1. Add property to initial state constant in `src/data/const.js`
2. Create property actions in `src/actions/index.jsx`
3. Create property reducer in `src/reducers/` and add it to the combinded reducer in `src/reducers/index.jsx`.
4. If this property should not be persisted in localstorage, add it to the list of properties that get cleaned when the state is saved, located in `src/index.jsx`
