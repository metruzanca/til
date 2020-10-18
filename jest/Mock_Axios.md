# Mocking Axios

Mocking Axios with jest is pretty straight forward.

First we need to import it into the test file, then we need to call jest.mock on the import string.

```js
import axios from 'axios'
jest.mock('axios')
```

After thats done we can simply mock the implementations as we need them and do our assertions e.g. toHaveBeenCalledWith (testing the response would be pointless as we've mocked that and we probably wanna check the the function which uses axios is returning what we expect it to return.)

```js
axios.mockImplementationOnce(() => Promise.resolve({data: foods}))
expect(axios).toHaveBeenCalledWith('/warehouse-service/id/foods-availability')
```