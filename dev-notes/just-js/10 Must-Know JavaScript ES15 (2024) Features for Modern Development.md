link: https://dev.to/manojspace/10-must-know-javascript-es15-features-for-modern-development-59hf

## 1. Array.prototype.groupBy()

The `groupBy()` method allows you to group elements in an array based on a given callback function.

```
// ES15
const people = [
  { name: 'Alice', age: 30 },
  { name: 'Bob', age: 25 },
  { name: 'Charlie', age: 30 },
  { name: 'David', age: 25 },
];

const groupedByAge = people.groupBy(person => person.age);
console.log(groupedByAge);

// Output:
// {
//   25: [{ name: 'Bob', age: 25 }, { name: 'David', age: 25 }],
//   30: [{ name: 'Alice', age: 30 }, { name: 'Charlie', age: 30 }]
// }

// Previous approach (ES6+)
const groupedByAgeOld = people.reduce((acc, person) => {
  if (!acc[person.age]) {
    acc[person.age] = [];
  }
  acc[person.age].push(person);
  return acc;
}, {});
```

## 2. Array.prototype.with()

