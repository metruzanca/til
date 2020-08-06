# Mocking Hooks used inside react components

After looking around the internet for how to mock a hook (specifically useParams), I found this nice implementation thats perfect for use when the hook is imported via destructuring.
```javascript
export const MockUseParams = () => ({
  // use actual for all non-hook parts
  ...jest.requireActual('react-router-dom'),
  useParams: () => ({
    _id: 'fake-id1',
  }),
})
```
With this setup any other imports are ignored and hook mocks can easily be added. In this case I've only mocked useParams.

Inside of my test file, I then added a call to jest.mock like this
```javascript
beforeEach(() => {
  jest.mock('react-router-dom', () => MockUseParams)
})
```
