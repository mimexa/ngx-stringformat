# ngx-stringformat  
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](./LICENSE.md)

> Useful pipe for Angular inspired by the java.util.lang.format() method

## Table of contents

 - [Installation](#installation)
 - [Contributing](#contributing)
 - [Changelog](CHANGELOG.md)
 - [String](#string)
 - [Number](#number)

 ## Installation

1. Use npm to install the package

  ```terminal
  $ npm install ngx-stringformat --save 
  ```

2. Add into your module `imports` the `NgStringFormatModule` in order to add the pipe.

  ```typescript
  import {NgStringFormatModule} from 'ngx-stringformat';
  
  @NgModule({
   // ...
   imports: [
     // ...
     NgStringFormatModule
   ]
  })
  ```

3. Pipes are also injectable and can be used in Components / Services / etc..

  ```typescript  
  import {StringFormat} from 'ngx-stringformat';

  @Component({
    // ..
    providers: [StringFormat]
  })
  export class AppComponent {
    constructor(private stringFormat: StringFormat) {
      this.stringFormat.transform('%s %s' | 'Hello' : 'world'); // Returns: "Hello world"
    }
    // ..
  }
  ```

## String

## Number
