# google-sheets-gpt

## Additional Code Needed

We need to add this to Google Apps Script.

```
function GPT(inputString, cellRange) {
  const url = 'URL'; // Replace with your API endpoint

  // cellRange is already an array of values
  const rangeValues = cellRange;
  
  // Flatten the range values into a single array if needed
  const flattenedValues = rangeValues.flat();

  const payload = {
    'event': flattenedValues,
    'location': flattenedValues,
    'clothing': flattenedValues,
    'time': flattenedValues,
    'nudity': flattenedValues,
    'emotion': flattenedValues,
    'dynamic': flattenedValues,
    'num': flattenedValues,
  };

  const options = {
    'method': 'post',
    'contentType': 'application/json',
    'payload': JSON.stringify(payload)
  };

  try {
    const response = UrlFetchApp.fetch(url, options);
    const json = response.getContentText();
    const data = JSON.parse(json);

    // Assuming the API response has a field named 'result'
    return data.result;
  } catch (error) {
    return 'Error: ' + error.message;
  }
}
```