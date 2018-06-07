# node-storage

# Install
```
npm install extra-local-storage
```

# Usage
```
import storage from 'extra-local-storage'
// store data in **'./test'**, default is 'storage'
const test = storage('test')
test.xxx // call api

// each storage also can be a function to create a sub-storage, it will store data in **'./test/test1'**
const test1 = test('test1') // 
test1.xxx // call api

```

# API
## Instance
1. storage(dir, opts)
a. opts.throws # if throws errors
b. opts.max # the max number of item in this storage
c. opts.ttl # the default ttl of each items
d. interval # the interval time to check ttl items

## Original API as localStorage in browser (**Sync**)
1. storage.length
2. storage.key(*index*)
3. storage.getItem(*key*)
4. storage.setItem(*key, value, opts*) # set *opts.ttl* as the **time to live**
5. storage.removeItem(*key*)
6. storage.clear(*all*) # if [*all*] is true, remove the dir itself including all sub-dirs

## Extra API (**Async**)
1. storage.get(*key*).then((*value*) => {})
2. storage.set(*key, value, opts*).then(() => {})
3. storage.remove(*key*).then(() => {})
4. storage.list().then((*[{key: value}, ...]*) => {})
5. storage.valueOf().then((*{key: value, ...}*) => {})
6. storage.cleanup(*all*).then(() => {}) # if[*all*] is true, remove the dir itself including all sub-dirs
7. storage.cleanout().then(() => {}) # remove all of the outdated items
