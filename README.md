# react-sk-countdown

##这是什么(What is it)
这是为react提供的一个验证码倒计时的组件

##如何使用（How to use it）

1. `npm install react-sk-countdown@latest --save`

```javascript

var React =require('react')

var {CountDownText} = require('react-sk-countdown');
export default class MyIntergral extends React.Component {
  constructor(props) {
      super(props)
      this.state = {
          countingDone:false,
      }
  }
  
  _sendVerifyCode(){
    this.setState({
      countingDone:false
    })
  }
  render() {
     var styleObj = {
            color:"#fff",
            fontSize:16,
            fontWeight:"normal",
            textAlign:"center",
            margin:'0 auto',
            background:"#ee735c",
            width:120,
            height:40,
            lineHeight:'40px',
            marginTop:10,
        } 
    return (
        <div>
         
              {
                this.state.countingDone
                ?<p style={styleObj} onClick={this._sendVerifyCode.bind(this)}>获取验证码</p>
                : <CountDownText
                style={styleObj}
                countType='seconds' // 计时类型：seconds / date 
                auto={true} // 自动开始 
                afterEnd={() => {this.setState({
                  countingDone:true
                })}} // 结束回调
                timeLeft={5} // 正向计时 时间起点为0秒 
                step={-1} // 计时步长，以秒为单位，正数则为正计时，负数为倒计时 
                startText='获取验证码' // 开始的文本 
                endText='获取验证码' // 结束的文本 
                intervalText={(sec) => sec + '秒重新获取'} // 定时的文本回调 
                />
              }
        </div>
    )
  }
}

```
![](https://github.com/songhaoreact/react-sk-countdown/blob/master/demo1.gif)
