﻿# ngx-stringformat  
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](./LICENSE.md)

> Useful pipe for [Angular](https://angular.io/) inspired by the [java.util.lang.format()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#format(java.lang.String,%20java.lang.Object...)) method

Try the StringFormat pipe online using [this website](https://string.surge.sh)

## Table of contents

 - [Installation](#installation)
 - [String](#string)
 - [Number](#number)
 - [Error management](#error)

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

  @Component()
  export class AppComponent {
    constructor(private stringFormat: StringFormat) {}
    // ..
  }
  ```

## Strings: Use stringFormat for string formatting

### Typescript

  ```typescript  
  this.stringFormat.transform('My name is %s' | 'Sam' );
  // Returns: "My name is sam"
  
  this.stringFormat.transform('Hi %2$s %1$s' | 'Norris' : 'Chuck');
  // Returns: "Hi Chuck Norris"
  
  this.stringFormat.transform('Dear %10s %10s' | 'Chuck' : 'Norris');
  // Returns: "Dear           Chuck          Norris"
  ```

### Html

  ```html  
  {{ 'My name is %s' | stringFormat : 'Sam' }}
  <!-- Display: "My name is sam" -->

  {{ 'Hi %2$s %1$s' | stringFormat : 'Norris' : 'Chuck' }}
  <!-- Display: "Hi Chuck Norris" -->

  {{ 'Dear %10s %10s' | stringFormat : 'Chuck' : 'Norris' }}
  <!-- Display: "Dear           Chuck          Norris" -->
  ```

## Numbers: Use stringFormat pipe for number formatting

### Typescript

  ```typescript  
  this.stringFormat.transform('%d karat of magic in the air' | 24 );
  // Returns: 24.00 karat magic of magic in the air"
  
  this.stringFormat.transform('%d karat of magic in the air' | '24' );
  // Returns: 24.00 karat magic of magic in the air"
  
  this.stringFormat.transform('%2$d+%2$d=%1$d' | 2 : 1);
  // Returns: "1.00+1.00=2.00"
  
  this.stringFormat.transform('I am %.0d years old' | 36);
  // Returns: "I am 36 years old"
  
  this.stringFormat.transform('My rate is:%10' | 120);
  // Returns: "My rate is:       120"
  ```

### Html

  ```html  
  {{ '%d karat of magic in the air' | stringFormat : 24 }}
  <!-- Display: "24.00 karat magic of magic in the air" -->

  {{ '%d karat of magic in the air' | stringFormat : '24' }}
  <!-- Display: "24.00 karat magic of magic in the air" -->

  {{ '%2$d+%2$d=%1$d' | stringFormat : 2 : 1 }}
  <!-- Display: "1.00+1.00=2.00" -->

  {{ 'I am %.0d years old' | stringFormat : 36 }}
  <!-- Display: "I am 36 years old" -->

  {{ 'My rate is:%10' | stringFormat : 120 }}
  <!-- Display: "My rate is:       120" -->
  ```

## Error management
  
### Index not found
  
  ```typescript  
  this.stringFormat.transform('Hi %2$s %1$s' | 'Norris' : 'Chuck');
  // Returns: "Hi Chuck [Error! Cannot find value in args for placeholder n°2]"
  ```

### Cannot parse number

  ```typescript  
  this.stringFormat.transform('I am %.0d years old' | 36y );
  // Returns: "I am [Error! Cannot parse value as a number: (36y)] years old"
  ```
