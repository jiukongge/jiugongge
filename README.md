# jiugongge
九宫格

- (void) createAppLoadView{
    //九宫格算法
    for (int i =0 ; i< self.appArray.count; i ++) {
        //初始化控件
        CZAppView *appView = [[CZAppView alloc]init];
        //将数据传递给控件
        appView.app = self.appArray[i];
        //计算  当前行 = i / 需要展现的列数
        int row = i / KAppColCount;
        //计算  当前列 = i % 需要展现的列数
        int col = i % KAppColCount;
        //获取当前界面的宽高属性
        UIScreen *screent = [UIScreen mainScreen];
        //计算列与列之间的间隔
        CGFloat magin = (screent.bounds.size.width - appView.bounds.size.width * KAppColCount)/(KAppColCount + 1);
        //计算控件的X   X = 间距 + 列 * (间距 + 控件的宽)
        CGFloat appViewX = magin + col * (magin + appView.bounds.size.width);
        //计算控件的Y   Y = 间距 + 行 * (间距 + 控件的高)
        CGFloat appViewY = magin + row * (magin + appView.bounds.size.height);
        //设置控件的frame
        appView.frame = CGRectMake(appViewX, appViewY, appView.bounds.size.width, appView.bounds.size.height);
        //将自定义的控件添加到当前的界面中
        [self.view addSubview:appView];
    }
