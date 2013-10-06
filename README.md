mongo-scripts
=============

Some usefull handy scripts

### Map/reduce scripts

**View value types of a field**
```javascript
col = 'test_col'; field = 'field';

db[col].mapReduce(function(){
  emit(this[f] == null ? typeof this[f] : this[f].constructor.name, 1);
}, function(k, vs){ return Array.sum(vs);}, {
  out: {inline: 1},
  scope:{f:field}
}).results;

```
