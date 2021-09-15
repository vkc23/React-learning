# React-learning

# Call child function component from parent component
<details>
  <summary>Child To Parent</summary>
  
  ```
import React, {
  Component,
  createRef,
  forwardRef,
  useRef,
  useImperativeHandle
} from 'react';

// use class Component

// class Parent extends Component {
//   constructor(props) {
//     super(props);
//     this.childRef = createRef();
//   }

//   render() {
//     return (
//       <div>
//         <h1>parent Component</h1>
//         <button onClick={() => this.childRef.current.childFunc()}>click</button>
//         <Child ref={this.childRef} />
//       </div>
//     );
//   }
// }

// class Child extends Component {
//   childFunc = () => {
//     alert('child call!');
//     console.log('child call!');
//   };

//   render() {
//     return <h1>child Component</h1>;
//   }
// }

// use function Component as Hooks

const Child = forwardRef((props, ref) => {
  useImperativeHandle(ref, () => ({
    childFunc() {
      alert('child call!');
      console.log('child call!');
    }
  }));
  return <h1>Child</h1>;
});

const Parent = () => {
  const childRef = useRef();
  return (
    <div>
      <h1>Parent</h1>
      <Child ref={childRef} />
      <button onClick={() => childRef.current.childFunc()}> click</button>
    </div>
  );
};
export default Parent;

```
</details>