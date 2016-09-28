# Complex List

# Build the container

```javascript
import React, {Component, PropTypes} from "react";

class ComplexListContainer extends Component {
  static propTypes = {
    data: PropTypes.object.isRequired,
    demoAction: PropTypes.func.isRequired,
  };

  render() {
    const {data, demoAction} = this.props;
    return <ComplexList items={data.items} demoAction={demoAction} />;
  }
}

function mapStateToProps({data}) {
  return {data};
}

function mapDispatchToProps(dispatch) {
  return {
    demoAction: () => dispatch(actions.demoAction()),
  };
}

export default connect(mapStateToProps, mapDispatchToProps)(ComplexListContainer);
```


# Build the list component

```javascript
export default class ComplexList extends Component {
  static propTypes = {
    items: Proptypes.array.isRequired,
    demoAction: PropTypes.func.isRequired,
  };

  constructor(props) {
    super(props);

    // Bindings
    this._complexListItems = this._complexListItems.bind(this);
  }

  _complexListItems() {
    const {items} = this.props.data;
    return items.forEach( (item) => <ComplexListItem item={item} );
  }

  render() {
    return this._complexListItems();
  }
}
```

# Build the list item Component

```javascript
export default function ComplextListItem(props) {
  const {message} = props;
  return <li>{message}</li>;
}
```
