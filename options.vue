provide​
Provide values that can be injected by descendant components.

Type

ts
interface ComponentOptions {
  provide?: object | ((this: ComponentPublicInstance) => object)
}
Details

provide and inject are used together to allow an ancestor component to serve as a dependency injector for all its descendants, regardless of how deep the component hierarchy is, as long as they are in the same parent chain.

The provide option should be either an object or a function that returns an object. This object contains the properties that are available for injection into its descendants. You can use Symbols as keys in this object.

Example

Basic usage:

js
const s = Symbol()

export default {
  provide: {
    foo: 'foo',
    [s]: 'bar'
  }
}
Using a function to provide per-component state:

js
export default {
  data() {
    return {
      msg: 'foo'
    }
  }
  provide() {
    return {
      msg: this.msg
    }
  }
}
Note in the above example, the provided msg will NOT be reactive. See Working with Reactivity for more details.

See also Provide / Inject
