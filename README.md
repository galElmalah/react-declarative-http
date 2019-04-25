# REACT-DECLARATIVE-FETCH

## What

A Declarative Way To Make HTTP Requests in React.

## Why

The process of making external API requests in a react component often repeats itself and I found myself handling the same state changes in different components to many times.  
For example, showing a `<Loader />`
component while fetching and taking into account the different responses from the API i.e Error or Success.

## How

In most cases, when making an async external call from a component you will want to account for three different phases in the request lifecycle:

1. **Fetching**
2. **Success**
3. **Error**

_REACT-DECLARATIVE-FETCH_ aims to give a dead simple and declarative API for handling the different state changes.
<br>  
**example**

```javascript
import { Fetch } from 'react-declarative-fetch';
const ImageGallery = () => {
  return (
    <Fetch url="someImageApiUrl">
      <Fetch.Error>Error while loading the images</Fetch.Error>
      <Fetch.Fetching>show loader</Fetch.Fetching>
      <Fetch.Success>
        {data => data.map(img => <Image {...img} />)}
      </Fetch.Success>
    </Fetch>
  );
};
```

## API

Both `<Fetch.Success>` and `<Fetch.Error>` can be used as a render props and they will be invoked with the response data or the Error passed to them.

### Props

| Name      | type    | Required                      | Description                                                                                        |
| --------- | ------- | ----------------------------- | -------------------------------------------------------------------------------------------------- |
| url       | string  | yes                           | the url to make the request from                                                                   |
| options   | object  | no, the default method is GET | options to pass to the request agent (i.e axios) like method, headers, etc...                      |
| withCache | boolean | no                            | if present the results would be cached and would be retrieved from the cache on following requests |
| delay     | number  | no                            | delay the request X amount of milliseconds                                                         |
