# JsonWSM API Documentation

## Overview

JsonWSM is a lightweight JSON parser that provides a simple interface for working with JSON data in C++. It supports UTF-8 encoding and various data types.

## Basic Usage

```cpp
#include "JsonWSM/JsonParser.h"

// Create a JSON object from a string
WSM::JsonParser json("{\"name\": \"John\", \"age\": 30, \"pi\": 3.14f}");

// Access values
JsonValue name = json["name"];
JsonValue age = json["age"];
JsonValue pi = json["pi"];
```

## API Methods

### Constructors

- `JsonParser()` - Default constructor
- `JsonParser(const std::string& jsonStr)` - Constructor that parses JSON from a string

### Type Checking JsonParser Object

- `JsonType getType(const std::string& key)` - Get the type of a value
- `bool isBool(const std::string& key)` - Check if value is boolean
- `bool isInt(const std::string& key)` - Check if value is integer
- `bool isFloat(const std::string& key)` - Check if value is float
- `bool isDouble(const std::string& key)` - Check if value is double
- `bool isString(const std::string& key)` - Check if value is string
- `bool isArray(const std::string& key)` - Check if value is array
- `bool isObject(const std::string& key)` - Check if value is object
- `bool isNull(const std::string& key)` - Check if value is null

### Value Access

- `JsonValue operator[const std::string& key]` - Access value by key

### Type Checking JsonValue

- `bool isBool()` - Check if value is boolean
- `bool isInt()` - Check if value is integer
- `bool isLong()` - Check if value is Long
- `bool isFloat()` - Check if value is float
- `bool isDouble()` - Check if value is double
- `bool isString()` - Check if value is string
- `bool isArray()` - Check if value is array
- `bool isObject()` - Check if value is object
- `bool isNull()` - Check if value is null
- `JsonType getType()` - Get the type of a value

### Data Access JsonValue
- `bool getBool()` - Get if value is boolean
- `int getInt()` - Get if value is integer
- `long getLong()` - Get if value is Long
- `float getFloat()` - Get if value is float
- `double getDouble()` - Get if value is double
- `std::string getString()` - Get if value is string
- `std::shared_ptr<JsonArray> getArray()` - Get if value is array
- `std::shared_ptr<JsonObject> getObject` - Get if value is object




### Utility Methods

- `bool empty()` - Check if an object or array is empty
- `int getSize()` - Get the size of an object or array
- `bool hasField(const std::string& key)` - Check if a field exists
- `std::vector<std::string> getFields()` - Get all field names

## Supported Data Types

- Boolean (`true`, `false`)
- Integer (e.g., `42`)
- Float (e.g., `3.14f` or `3.14F` with up to 7 decimal places)
- Double (e.g., `3.14` or `3.14159265f` with more than 7 decimal places)
- String (e.g., `"hello"`)
- Array (e.g., `[1, 2, 3]`)
- Object (e.g., `{"key": "value"}`)
- Null

### Float Type Notes

- Float values must end with 'f' or 'F' suffix
- Maximum precision is 7 decimal places
- Values with more than 7 decimal places are automatically treated as double
- Examples:
  - `3.14f` - float
  - `1.234567f` - float
  - `1.2345678f` - double (exceeds 7 decimal places)
  - `3.14` - double (no suffix)

## Example Usage

```cpp
// Parse JSON
WSM::JsonMin json("{\"name\": \"John\", \"age\": 30, \"pi\": 3.14f, \"precise\": 1.2345678f}");

// Check types
if (json["name"].isString()) {
    std::string name = std::any_cast<std::string>(json["name"]);
}

if (json["age"].isInt()) {
    int age = std::any_cast<int>(json["age"]);
}

if (json["pi"].isFloat()) {
    float pi = std::any_cast<float>(json["pi"]);
}

if (json["precise"].isDouble()) {
    double precise = std::any_cast<double>(json["precise"]);
}

// Access nested values
WSM::JsonMin nested("{\"user\": {\"name\": \"John\", \"address\": {\"city\": \"New York\"}}}");
std::string city = nested["user"]["adress"]["city"].getString();

```
