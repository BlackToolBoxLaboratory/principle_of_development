# Developement protocol of Black Tool Box Laboratory

Here is out developmemnt protocol for black tool box laboratory.

Menu:
- [HTML's naming Rules](https://github.com/BlackToolBoxLaboratory/principle_of_development/blob/master/README.md#htmls-class-naming-rules-for-style-using)
- [JavaScript's Naming Rules](https://github.com/BlackToolBoxLaboratory/principle_of_development/blob/master/README.md#javascripts-naming-rules)
- [Logical Conventions](https://github.com/BlackToolBoxLaboratory/principle_of_development/blob/master/README.md#logical-conventions)


## HTML's class naming rules for style using

The class naming convention is based on [Block-Element-Modifier](http://getbem.com/). However we seperate it into Block_Element and Element-Modifier. Here is for example:

  ```js
  <div class="component-panel panel-collapsable"> // component's name
    <div class="panel_head head-gray-d">
      <p class="head_title">Title</p>
    </div>
    <div class="panel_body body-gray-ll">
      <input class="body_input input-name" placehold="What's your name?">
      <button class="body_submitBtn submitBtn-disabled" disabled>
        {{'Submit'}}
      </button>
    </div>
  </div>
  ```

## JavaScript's Naming Rules

### Constance

  - Definition: `const` variables should be named in format of Snake Case in UpperCase `[Any][?_Any]`, for examples: `ROUTE_MAIN`, `ROUTE_ABOUT_ME`.

### Function

  - Function: Normal function should be named in format of Camel Case `[verbe][Item name][?Descripted]Fn`, for exmaples: `renderMenuItemFn`, `renderListFn`, `updateItemHeightFn`.
  - Inner Function: Function which is used in component itself only should be named in format of Camel Case `_[verbe][Item name][?Descripted]Fn[?_recursive]`, for examples: `_transformTypeFn`, `_updateItemHeightFn_recursive`.

### Temporary Variable

  - Temporary variable: While in logical operations(ex: looping), the transition variable should be named with prefix `temp_`, for examples: `temp_activeObj`, `temp_counting`.

### Stringfied Variable

  - Stringfied variable: For some logic operation required, the stringfied variable should be named with postfix `_str`, for examples: `timestamp_str`. (stringfied json data is included)

### Variable: Object

  - Object: Except components, variables in Object should be named in format of Camel Case `[item name][?desctiption]Obj`, for examples: `userInfoObj`, `dataObj`.
  - Component: Component is Object, and it should be named in format of Upper Camel Case as well-known.

### Variable: Array

  - List: Variables in Array should be named in format of Camel Case `[item name][?desctiption]List`, for examples: `memberList`, `menuItemList`.

### Variable: String

  - String: Variables in String should be named in format of Camel Case `[item name][?desctiption]`, for examples: `name`, `description`.

### Variable: Numeric/Number

  - Numeric: Variables in String should be named in format of Camel Case. when the variable can not be recognized to numeric by its essential meaning, strongly suggest we should rename it precisely. However, if it is unavoidable. please append the `_Num` as postfix. `[item name][?desctiption]_Num`, for examples: `productID_Num`. (Means we should strickly realize the variable's definiton: Number or Numeric String. For example some company defined their productionID as Numeric, some defined it as Numeric String.)
  
## Logical Conventions

There are many ways to implement logic. However for more efficient on development and maintainace source code. Please using some function for specific purpose.

### switch & if-else

Please try to recognize those examples as following:

  - Switch

      ```js
      switch(errorCode)
      {
        case HTTP_STATUS_LIST.STATUS_OK:
          ...
          break
        case HTTP_STATUS_LIST.BAD_REQUEST:
        case HTTP_STATUS_LIST.BAD_GATEWAY:
          ...
          break
        default:
          ...
          break
      }
      ```

  - if-else

      ```js
      if(sensorHumidity < 30) {
        ...
      } else if ((sensorHumidity >= 30) && (sensorHumidity < 80)) {
        ...
      } else {
        ...
      }
      ```

### Function for Object and Array

To better code's readability. Please do not use the loop function of Object and Array mixedly There are rules needed to be followed:

  - for-loop 
  
    If the logic we needed is the find-loop in essential, please do not use for-loop. That is why we will see the `if-else` & `break` in those examples of for-loop.

    ```js
    // Array
    for(let index of array)
    {
      if(...) {
        ...
        break
      }
      ...
    }

    // object
    for(let [key, value] of Object.entries(obj))
    {
      if(...) {
        ...
        break
      }
      ...
    }
    ```

  - Please use the function of Array as its literal meaning: 
    
    - Array.forEach()
    - Array.map()
    - Array.find()
    - Array.filter()
    - Array.every()
    - Array.some()
    - Array.reduce()
