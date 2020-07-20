# javascript-functions

1. isAlphaNumeric
* this is about 50% faster than regex `/[0-9a-z]/.test(char)`
```
function isAlphaNumeric(char) {
    let code = char.charCodeAt(0)
    if(!(code > 47 && code < 58) && 
       !(code > 64 && code < 91) && 
       !(code > 96 && code < 123)) {
           return false;
       }
       return true;
}
```

2. getTimeMsg
```
  getTimeMsg(updatedAt) {
    const createdTime = new Date(updatedAt);
    const currentTime = new Date();
    const second = 60;
    const minute = 60;
    const hour = 24;
    const day = 30;
    const month = 12;
    let divider = 1;
    let timeMsg = '';
    let diff = (currentTime - createdTime) / 1000;
    if (diff <= second) {
      timeMsg = 'second';
    } else if (diff <= second * minute) {
      divider = second;
      timeMsg = 'minute';
    } else if (diff <= second * minute * hour) {
      divider = second * minute;
      timeMsg = 'hour';
    } else if (diff <= second * minute * hour * day) {
      divider = second * minute * hour;
      timeMsg = 'day';
    } else if (diff <= second * minute * hour * day * month) {
      divider = second * minute * hour * day;
      timeMsg = 'month';
    } else {
      divider = second * minute * hour * day * month;
      timeMsg = 'year';
    }
    diff /= divider;
    const displayTime = Math.abs(Math.round(diff));
    const plural = displayTime > 1 ? 's' : '';
    const timeMessage = `${displayTime} ${timeMsg}${plural} ago`;
    return timeMessage;
  }
```
  
3. randomFileName
```
randomFileName() {
    return Math.random().toString(36).substring(2) + Math.random().toString(36).substring(2)
};
```

4. textBolder
* return statement has react expression
```
  textBolder(text, boldStr) {
    const keyword = new RegExp(boldStr, 'i');
    const array = text.split(keyword);
    const keyIndex = text.toLowerCase().indexOf(boldStr.toLowerCase());
    const originalKeyword = text.substring(keyIndex, keyIndex + boldStr.length);
    return (
      <>
        {array.map((item, index) => (
          <span key={index}>
            {item}
            {index !== array.length - 1 && (
              <b className="text-warning">{originalKeyword}</b>
            )}
          </span>
        ))}
      </>
    );
  }
```

5. numberFormat
```
  numberFormat(number) {
    let like = 'like';
    let changedNumber = number;
    if (number > 1) like += 's';
    if (number >= 1e3 && number < 1e6) {
      changedNumber = +(number / 1e3).toFixed(1) + 'K';
    }
    if (number >= 1e6 && number < 1e9) {
      changedNumber = +(number / 1e6).toFixed(1) + 'M';
    }
    if (number >= 1e9 && number < 1e12) {
      changedNumber = +(number / 1e9).toFixed(1) + 'B';
    }
    if (number >= 1e12) {
      changedNumber = +(number / 1e12).toFixed(1) + 'T';
    }
    return `${changedNumber} ${like}`;
  }
```

