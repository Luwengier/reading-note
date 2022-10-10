<u>_ReactElement:_</u>
ReactElement is the **result of React.createElement() / jsx() function call**, and that is an object with a type and props.

    interface ReactElement<P = any, T extends string | JSXElementConstructor<any> = string | JSXElementConstructor<any>> {
        type: T;
        props: P;
        key: Key | null;
    }

<u>_JSX.Element:_</u>
JSX.Element is a ReactElement, with the generic type for props and type being any. It exists, as various libraries can implement JSX in their own way, therefore JSX is a global namespace that then gets set by the library, React sets it like this:

    declare global {
      namespace JSX {
        interface Element extends React.ReactElement<any, any> { }
      }
    }

<u>_ReactNode:_</u>
React node itself is a representation of the virtual DOM. So ReactNode is the set of **all possible return values of a component (including ReactElement)**.

    type ReactNode =
    ReactElement | string | number | ReactFragment | ReactPortal | boolean | null | undefined;

<br />

extra
<u>_FunctionComponent:_</u>
It is also return ReactElement when FunctionComponent called.

    interface FunctionComponent<P = {}> {
        (props: P, context?: any): ReactElement<any, any> | null;
        propTypes?: WeakValidationMap<P> | undefined;
        contextTypes?: ValidationMap<any> | undefined;
        defaultProps?: Partial<P> | undefined;
        displayName?: string | undefined;
    }

<br />

Reference:
[dev.io](https://dev.to/fromaline/jsxelement-vs-reactelement-vs-reactnode-2mh2)
[stock overflow](https://stackoverflow.com/questions/58123398/when-to-use-jsx-element-vs-reactnode-vs-reactelement)

[Typescript interface function](https://ithelp.ithome.com.tw/articles/10191476)
