- **React Component**
    - **元件初始化階段**
    
        - **[child\]**  getDefaultProps

    - **[mixin\]** getDefaultProps - 開始有預設的props (還沒得到來自parent的props)

    - getDefaultProps
    
    - **[mixin\]** contextTypes - 如果parent有符合的context, 應該從這邊開始會得到

    - contextTypes - this.context
 
    - **[mixin\]** getInitialState - 開始有this.state

    - getInitialState

    - componentWillMount - 仰賴state, 可是不需update的資料在此處理
    
    - getChildContext - 所以child在getDefaultProps時拿不到context

    - render
    
        - **[child\]**  getInitialState 這邊開始, child才會從parent得到props
        - **[child\]**  componentWillMount
        - **[child\]**  render

    - **從這之後只有Client Side會執行到**
    
        - **[child\]**  componentDidMount
    - **[mixin\]** componentDidMount
    - componentDidMount

    ---
    
    - **元件running階段** (正常來說, 只有this.state, this.props改變才會觸發更新)
    
    - componentWillUpdate (nextProps, nextState)

    - getChildContext
    
    - render
    
    - componentDidUpdate (prevProps, prevState)

    ---
    
    - **元件結束階段** (目前還沒處理到離開機制, 沒實際確認過會跑哪些)
    
    - componentWillUnmount 
    
    