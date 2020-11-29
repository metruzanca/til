```js
export function _prepareTimetable(timeTable) {
  const defaultTable = JSON.parse(JSON.stringify(DEFAULT_WEEK_TABLE));
  // eslint-disable-next-line array-callback-return
  timeTable.map((element) => {
    function isSameDay(day) {
      return day.id === element.day;
    }
    const defaultDay = defaultTable.find(isSameDay);
    if (defaultDay) {
      defaultDay.data = _prepareTimetableData(element.openingHours);
    }
  });
  return defaultTable;
}
```

```js
export function _prepareTimetable(timeTable) {
  const defaultTable = cloneDeep(DEFAULT_WEEK_TABLE);
  timeTable.forEach((element) => {
    const defaultDay = defaultTable.find((day) => day.id === element.day);
    if (defaultDay) {
      defaultDay.data = _prepareTimetableData(element.openingHours);
    }
  });
  return defaultTable;
}
```

```js
export function _prepareTimetable(timeTable){
  return DEFAULT_WEEK_TABLE.map(day => {
    const foundDay = timeTable.find((element) => day.id === element.day)
    if(foundDay?.openingHours !== undefined){
      return {
        ...day,
        data: _prepareTimetableData(foundDay.openingHours)
      }
    }
    return day
  })
}
```
