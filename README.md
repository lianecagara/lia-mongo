# LiaMongo

## Introduction

LiaMongo is a simplified MongoDB key-value store designed to make MongoDB operations easier for casual developers. It provides a straightforward interface for storing and retrieving key-value pairs in MongoDB collections.

## Rationale

Many developers find MongoDB's document-oriented approach flexible but sometimes overwhelming, especially for simple key-value storage scenarios. LiaMongo aims to simplify this process by abstracting away much of the complexity of interacting with MongoDB.

## Target Users

LiaMongo is targeted towards developers who need a simple and intuitive way to store key-value data in MongoDB without dealing with the intricacies of the MongoDB driver or schema design.

## Advantage of Easiness

The primary advantage of LiaMongo is its ease of use. By providing a straightforward API for common MongoDB operations, developers can quickly integrate LiaMongo into their projects without needing extensive knowledge of MongoDB internals.

## Disadvantage of Key-Value Schema

While the key-value schema provides simplicity and flexibility, it may not be suitable for all use cases, especially those requiring complex querying or relationships between data. Additionally, the lack of schema validation for the value field may lead to inconsistencies in data storage.

## Installation
```bash
npm install lia-mongo
```

## How to import
```js
const LiaMongo = require('lia-mongo');
```

## Methods

### Constructor

#### Description

Creates a new instance of LiaMongo.

#### Arguments

- `options`: An object containing configuration options.
  - `uri`: MongoDB connection URI.
  - `collection`: Name of the MongoDB collection to use.
  - `isOwnHost`: (Optional) Boolean indicating whether the MongoDB instance is hosted on the same machine. Default is `false`.
  - `ignoreError`: (Optional) Boolean indicating whether to ignore connection errors. Default is `false`.
  - `allowClear`: (Optional) Boolean indicating whether clearing the collection is allowed. Default is `false`.

#### Returns

A new instance of LiaMongo.

#### Usage

```javascript
const liaMongo = new LiaMongo({
  uri: "mongodb://localhost:27017/mydb",
  collection: "myCollection",
  isOwnHost: true,
});
```

### start()

#### Description

Connects to the MongoDB database.

#### Returns

Promise<void>.

#### Usage

```javascript
await liaMongo.start();
```

### get(key)

#### Description

Retrieves the value associated with the given key.

#### Arguments

- `key`: The key to retrieve the value for.

#### Returns

Promise<any> | null: The value associated with the key, or null if not found.

#### Usage

```javascript
const value = await liaMongo.get("myKey");
```

### put(key, value)

#### Description

Stores a key-value pair in the MongoDB collection.

#### Arguments

- `key`: The key to store.
- `value`: The value to store.

#### Returns

Promise<void>.

#### Usage

```javascript
await liaMongo.put("myKey", "myValue");
```

### remove(key)

#### Description

Removes the key-value pair with the given key from the MongoDB collection.

#### Arguments

- `key`: The key to remove.

#### Returns

Promise<void>.

#### Usage

```javascript
await liaMongo.remove("myKey");
```

### containsKey(key)

#### Description

Checks if the given key exists in the MongoDB collection.

#### Arguments

- `key`: The key to check.

#### Returns

Promise<boolean>: True if the key exists, false otherwise.

#### Usage

```javascript
const exists = await liaMongo.containsKey("myKey");
```

### size()

#### Description

Gets the number of key-value pairs in the MongoDB collection.

#### Returns

Promise<number>: The number of key-value pairs.

#### Usage

```javascript
const size = await liaMongo.size();
```

### clear()

#### Description

Clears all key-value pairs from the MongoDB collection.

#### Returns

Promise<void>.

#### Usage

```javascript
await liaMongo.clear();
```

### keys()

#### Description

Retrieves an array of all keys in the MongoDB collection.

#### Returns

Promise<string[]>: An array of keys.

#### Usage

```javascript
const keys = await liaMongo.keys();
```

### values()

#### Description

Retrieves an array of all values in the MongoDB collection.

#### Returns

Promise<any[]>: An array of values.

#### Usage

```javascript
const values = await liaMongo.values();
```

### entries()

#### Description

Retrieves an array of all key-value pairs in the MongoDB collection.

#### Returns

Promise<{ key: string, value: any }[]>: An array of key-value pairs.

#### Usage

```javascript
const entries = await liaMongo.entries();
```

### load()

#### Description

Loads all key-value pairs from the MongoDB collection into an object.

#### Returns

Promise<object>: An object containing all key-value pairs.

#### Usage

```javascript
const data = await liaMongo.load();
```

### preProc()

#### Description

Pre-processes the given data.

#### Arguments

- `data`: The data to pre-process.

#### Returns

Promise<object>: The pre-processed data.

#### Usage

```javascript
const preProcessedData = await liaMongo.preProc(data);
```

### toObject()

#### Description

Converts all key-value pairs in the MongoDB collection into an object.

#### Returns

Promise<object>: An object containing all key-value pairs.

#### Usage

```javascript
const objectData = await liaMongo.toObject();
```

### Static Schema

#### Description

The schema used for storing key-value pairs in MongoDB.

#### Usage

```javascript
LiaMongo.schema;
```

## Credits

LiaMongo npm package created by Liane Cagara.
