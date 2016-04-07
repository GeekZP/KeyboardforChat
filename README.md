# KeyboardForChat
仿微信聊天键盘。  
优点：无污染，无任何第三方，使用简单。

博客：[devcai.com](http://devcai.com)  

  qq: 2581502433@qq.com

# 控件使用效果
![](2016-04-02 11_31_12.gif)

# 控件使用步骤

## 代码
1. 导入KeyBoard文件夹  
2. 资源文件是 emotion.plist 和 face.plist 图片在 Assets.xcassets
3. 导入ChatKeyBoard.h即可使用，具体参考demo

## 添加数据源
```objc
    // 使用 keyBoard 默认导航栏是透明的
    self.chatKeyBoard = [ChatKeyBoard keyBoard];
    
    // 如果导航栏不透明，请使用 + (instancetype)keyBoardWithNavgationBarTranslucent:(BOOL)translucent;
    // self.chatKeyBoard = [ChatKeyBoard keyBoardWithNavgationBarTranslucent:NO];

    self.chatKeyBoard.delegate = self;
    self.chatKeyBoard.dataSource = self;
    
    //可以设置placeHolder
    self.chatKeyBoard.placeHolder = @"请输入消息，请输入消息，请输入消息，请输入消息，请输入消息，请输入消息，请输入消息，请输入消息";
    /**
     *  placeHolderColor 默认是 浅灰色
     */
    //self.chatKeyBoard.placeHolderColor = [UIColor redColor];
    
    [self.view addSubview:self.chatKeyBoard];
```

## 实现数据源代理
```objc
- (NSArray<MoreItem *> *)chatKeyBoardMorePanelItems
{
    MoreItem *item1 = [MoreItem moreItemWithPicName:@"sharemore_location" highLightPicName:nil itemName:@"位置"];
    MoreItem *item2 = [MoreItem moreItemWithPicName:@"sharemore_pic" highLightPicName:nil itemName:@"图片"];
    MoreItem *item3 = [MoreItem moreItemWithPicName:@"sharemore_video" highLightPicName:nil itemName:@"拍照"];
    MoreItem *item4 = [MoreItem moreItemWithPicName:@"sharemore_location" highLightPicName:nil itemName:@"位置"];
    MoreItem *item5 = [MoreItem moreItemWithPicName:@"sharemore_pic" highLightPicName:nil itemName:@"图片"];
    MoreItem *item6 = [MoreItem moreItemWithPicName:@"sharemore_video" highLightPicName:nil itemName:@"拍照"];
    MoreItem *item7 = [MoreItem moreItemWithPicName:@"sharemore_location" highLightPicName:nil itemName:@"位置"];
    MoreItem *item8 = [MoreItem moreItemWithPicName:@"sharemore_pic" highLightPicName:nil itemName:@"图片"];
    MoreItem *item9 = [MoreItem moreItemWithPicName:@"sharemore_video" highLightPicName:nil itemName:@"拍照"];
    return @[item1, item2, item3, item4, item5, item6, item7, item8, item9];
}
- (NSArray<ChatToolBarItem *> *)chatKeyBoardToolbarItems
{
    ChatToolBarItem *item1 = [ChatToolBarItem barItemWithKind:kBarItemFace normal:@"face" high:@"face_HL" select:@"keyboard"];
    
    ChatToolBarItem *item2 = [ChatToolBarItem barItemWithKind:kBarItemVoice normal:@"voice" high:@"voice_HL" select:@"keyboard"];
    
    ChatToolBarItem *item3 = [ChatToolBarItem barItemWithKind:kBarItemMore normal:@"more_ios" high:@"more_ios_HL" select:nil];
    
    ChatToolBarItem *item4 = [ChatToolBarItem barItemWithKind:kBarItemSwitchBar normal:@"switchDown" high:nil select:nil];
    
    return @[item1, item2, item3, item4];
}

- (NSArray<FaceSubjectModel *> *)chatKeyBoardFacePanelSubjectItems
{
    return [FaceSourceManager loadFaceSource];
}
```

##控件里面的一些View可以自己定制，里面只是稍微演示
`PanelBottomView`
`OfficialAccountToolbar`

##控件可以根据业务需要，更换业务模型
`MoreItem`  
`ChatToolBarItem`  
`FaceSubjectModel`   
`FaceSourceManager`   

##感谢  
`MessageDisplayKit`
