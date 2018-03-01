### Within screens/Units.js

`componentDidMount` from screens/Units.js is adding our local method `_handleEditNav` and local state `assessment` from the Unit.js class. 

```javascript
// screens/Units.js
componentDidMount() {

  const { assessment } = this.state

  this.props.navigation.setParams({
    handleEditNav: this._handleEditNav,
    assessment
  })

}
```

`_handleEditNav` is the local method being used passed to the EditButton component. This might not be neccesary if the component is created in-line within `static navigationOptions`

```javascript
_handleEditNav(route, params, action) {
  this.props.navigation.navigate(route, params, action)
}
```

We use `static navigationOptions` to add `assessment` (local assessment state from Units.js class) as well as `handleEditNav`, which lets us call `navigate` from the component that we're inserting in `headerRight`. In this context, EditButton is a component declared outside of Units.js

```javascript
// screens/Units.js
static navigationOptions = ({ navigation }) => {

  const { params = {} } = navigation.state

  const { assessment, handleEditNav } = params

  return {
    headerRight: (
      <EditButton
        assessment={assessment}
        handleEditNav={handleEditNav}
      />
    )
  }
}
```

Finally, this is the component being passed into the nav header. Its props get populated from within `static navigationOptions`

```javascript
// EditButton.js component insterted into nav header
// This could also be a fxn component
class EditButton extends Component {
  render() {
    
    const { assessment, handleSetParams, handleEditNav } = this.props
    
    const onPress = () => {
      handleEditNav('EditUnit', assessment)
    }

    return <Button title="edit" onPress={onPress}/>
  }
}
```

```
navigation.navigate({ routeName, params, action })
```

I'm using the navigate method's 2nd arg to pass the local assessment state.
