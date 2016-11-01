# ZJUsefulPickerView
一个很有用的pickerView, 能够快速方便的弹出单列, 多列不关联, 多列关联数据的pickerView, 同时提供省市区联动的pickerView, 日期选择pickerView. 


![pickerView.gif](http://upload-images.jianshu.io/upload_images/1271831-0ce97c5e45557934.gif?imageMogr2/auto-orient/strip)

```
          [ZJUsefulPickerView showSingleColPickerWithToolBarText:@"单列数据" withData:@[@"objective-C", @"swift", @"iOS", @"iPad", @"iPod", @"mac", @"java", @"php", @"JavaScript"] withDefaultIndex:3 withCancelHandler:^{
                NSLog(@"quxiaole -----");
                
            } withDoneHandler:^(NSInteger selectedIndex, NSString *selectedValue) {
                NSLog(@"%@---%ld", selectedValue, selectedIndex);
                
            }];
            
            // 省市区选择
            [ZJUsefulPickerView showCitiesPickerWithToolBarText:@"省市区选择" withDefaultSelectedValues:@[@"四川", @"成都", @"郫县"] withCancelHandler:^{
                NSLog(@"quxiaole -----");

            } withDoneHandler:^(NSArray *selectedValues) {
                NSLog(@"%@---", selectedValues);

            }];
```

* 多列关联数据的显示, 注意数据的格式.

```
            NSArray *multipleAssociatedData = @[// 数组
                                                @[@"交通工具", @"食品", @"游戏"], //这是第一列  --- 数组
                                                
                                                @{   /*key- 第一列中的   value(数组) --> 对应的第二类的数据 */
                                                    @"交通工具": @[@"陆地", @"空中", @"水上"],//字典
                                                    @"食品": @[@"健康食品", @"垃圾食品"],
                                                    @"游戏": @[@"益智游戏", @"角色游戏"]
                                                  
                                                },
                                                
                                                @{ /*key- 第二列中的   value(数组) --> 对应的第三类的数据 */
                                                     @"陆地": @[@"公交车", @"小轿车", @"自行车"],
                                                     @"空中": @[@"飞机"],
                                                     @"水上": @[@"轮船"],
                                                     @"健康食品": @[@"蔬菜", @"水果"],
                                                     @"垃圾食品": @[@"辣条", @"不健康小吃"],
                                                     @"益智游戏": @[@"消消乐", @"消灭星星"],
                                                     @"角色游戏": @[@"lol", @"cf"]
                                                     
                                                }
                                                // .......

                                            ];
            [ZJUsefulPickerView showMultipleAssociatedColPickerWithToolBarText:@"多列关联数据-- 注意格式" withDefaultValues:@[@"交通工具", @"空中"] withData:multipleAssociatedData withCancelHandler:^{
                NSLog(@"quxiaole -----");

            } withDoneHandler:^(NSArray *selectedValues) {
                NSLog(@"%@---", selectedValues);
            }];
```