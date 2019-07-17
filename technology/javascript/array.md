# Array

## Filter

### Remove duplicates

```javascript
const categories = ['A', 'A', 'B', 'C']

var result = categories.filter(function(c, i){
  return categories.indexOf(c) >= i;
});

// result => ['A', 'B', 'C']
```

