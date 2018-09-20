# react-native-scrollable-container
基于React Native官方组件ScrollView与React-Navigation实现headerTitle与界面的滑动的交互效果

## Installation

```bash
npm install react-native-scrollable-container --save
```

## Import into your project

```js
import ScrollContainer from 'react-native-scrollable-container';
```

## Examle useage

```js
static navigationOptions = ({ navigation }) => ({
  ...ThemeStyles.indexHeaderStyle,
  headerTitleStyle: {
    ...ThemeStyles.indexHeaderStyle.headerTitleStyle,
    opacity: navigation.getParam('opacity', new Animated.Value(0)),
  },
  headerTitle: navigation.getParam('title', ''),
});
```
```js
<ScrollContainer title="个人中心" navigation={this.props.navigation} scrollOffset={this.state.scrollOffset}>
  <Header
    onLayout={(e) => { this.setState({ scrollOffset: e.nativeEvent.layout.height - px2dp(18) }) }}
    title="个人中心"
    iconName="cog"
    onPress={() => this.props.navigation.navigate('settings')}
  />
  {this.renderUserInfo()}
  {this.renderOptions()}
</ScrollContainer>
```

## Properties

属性  | 描述    | 类型  | 默认    
------ | ------ | ------  | ------
title  | 导航栏标题 | ``` PropTypes.string.isRequired ``` | 标题
scrollOffset | 滑动距离阀值  | ``` PropTypes.number.isRequired ``` | 0  
style | 样式  | ``` PropTypes.oneOfType([ PropTypes.object, PropTypes.number ]) ```  | ``` { flex: 1, backgroundColor: '#F7F7F7' } ``` 
navigation | 导航属性  | ``` PropTypes.object.isRequired ```  | 必填，否则无法控制导航，实现交互效果 
