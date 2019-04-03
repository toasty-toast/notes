# WPF

## Filtering a Collection Without Modifying It

```C#
private ObservableCollection<string> myBackingCollection = new ObservableCollection<string>();
public ICollectionView MyCollectionView
{
    get
    {
        ICollectionView view = CollectionViewSource.GetDefaultView(this.myBackingColleciton);
        view.Filter = (obj) => true; // Filter delegate
        return view;
    }
}
```

## Remove Toolbar Grip and Overflow

XAML
```WPF
<ToolBarPanel DockPanel.Dock="Top">
    <ToolBar ToolBarTray.IsLocked="True" Loaded="ToolBar_Loaded">
        <Menu ToolBar.OverflowMode="Never">
            <!-- Menu items -->
        </Menu>
    </ToolBar>
</ToolBarPanel>
```

Code behind
```C#
private void ToolBar_Loaded(object sender, RoutedEventArgs e)
{
    ToolBar toolBar = sender as ToolBar;
    var overflowGrid = toolBar.Template.FindName("OverflowGrid", toolBar) as FrameworkElement;
    if (overflowGrid != null)
    {
        overflowGrid.Visibility = Visibility.Collapsed;
    }
    var mainPanelBorder = toolBar.Template.FindName("MainPanelBorder", toolBar) as FrameworkElement;
    if (mainPanelBorder != null)
    {
        mainPanelBorder.Margin = new Thickness();
    }
}
```

## Span All Grid Rows and Columns

The following code shows how to make a control span all rows and/or columns of its parent grid, even if the number of rows and columns change.

```WPF
<Grid>
    <!-- Other stuff in the grid -->
    <ContentControl Grid.RowSpan="{Binding RelativeSource={RelativeSource AncestorType=Grid},  Path=RowDefinitions.Count, Mode=OneWay}"
                    Grid.ColumnSpan="{Binding RelativeSource={RelativeSource AncestorType=Grid},  Path=ColumnDefinitions.Count, Mode=OneWay}"/>
</Grid>
```
