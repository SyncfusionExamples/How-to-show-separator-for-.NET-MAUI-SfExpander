# How to show separator for .NET MAUI SfExpander?
This article demonstrates how to show separator for [.NET MAUI SfExpander](https://www.syncfusion.com/maui-controls/maui-expander). This example shows how to add a separator for [SfExpander.Header](https://help.syncfusion.com/cr/maui/Syncfusion.maui.Expander.SfExpander.html#Syncfusion_Maui_Expander_SfExpander_Header) and [SfExpander.Content](https://help.syncfusion.com/cr/maui/Syncfusion.maui.Expander.SfExpander.html#Syncfusion_Maui_Expander_SfExpander_Content) by using BoxView in [SfExpander](https://www.syncfusion.com/maui-controls/maui-expander).

**XAML:**

BoxView added in Header and Content with Height as 2. Converter bound to the IsVisible property to change the visibility of the separator line and the ConverterParameter defined by Header and Content.

 ```xml
   <ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:syncfusion="clr-namespace:Syncfusion.Maui.Expander;assembly=Syncfusion.Maui.Expander"
             xmlns:local="clr-namespace:SfExpander_Sample.Helper"
             x:Class="SfExpander_Sample.MainPage" Padding="0,15,0,0">

    <ContentPage.Resources>
        <ResourceDictionary>
            <local:ExpanderIconConverter x:Key="ExpanderIconConverter"/>
            <local:SeperatorVisibilityConverter x:Key="SeperatorVisibilityConverter"/>
        </ResourceDictionary>
    </ContentPage.Resources>

    <ContentPage.Content>
        <ScrollView BackgroundColor="#EDF2F5">
            <StackLayout>
                <syncfusion:SfExpander x:Name="expander1" HeaderIconPosition="None">
                    <syncfusion:SfExpander.Header>
                        <Grid>
                            <Grid.RowDefinitions>
                                <RowDefinition Height="50"/>
                                <RowDefinition Height="2"/>
                            </Grid.RowDefinitions>
                            <Grid>
                                <Label Text="Veg Pizza" VerticalTextAlignment="Center" Margin="10,0,0,0"/>
                                <Image Margin="10" HorizontalOptions="End" HeightRequest="15" WidthRequest="15" Source="{Binding IsExpanded,Source={x:Reference expander1},Converter={StaticResource ExpanderIconConverter}}"/>
                            </Grid>
                            <BoxView Grid.Row="1" IsVisible="{Binding Path=IsExpanded, Source={x:Reference expander1}, Converter={StaticResource SeperatorVisibilityConverter}, ConverterParameter='Header'}" BackgroundColor="#1565c0"/>
                        </Grid>
                    </syncfusion:SfExpander.Header>
                    <syncfusion:SfExpander.Content>
                        <Grid BackgroundColor="#FFFFFF">
                            <Grid.RowDefinitions>
                                <RowDefinition Height="Auto"/>
                                <RowDefinition Height="2"/>
                            </Grid.RowDefinitions>
                            <Label BackgroundColor="#FFFFFF" HeightRequest="50" Text="Veg pizza is prepared with the items that meet vegetarian standards by not including any meat or animal tissue products." TextColor="#303030" Margin="10,10,10,10" VerticalTextAlignment="Center"/>
                            <BoxView Grid.Row="1" IsVisible="{Binding Path=IsExpanded, Source={x:Reference expander1}, Converter={StaticResource SeperatorVisibilityConverter}, ConverterParameter='Content'}" BackgroundColor="#1565c0"/>
                        </Grid>
                    </syncfusion:SfExpander.Content>
                </syncfusion:SfExpander>

                <syncfusion:SfExpander x:Name="expander2" HeaderIconPosition="None">
                    <syncfusion:SfExpander.Header>
                        <Grid>
                            <Grid.RowDefinitions>
                                <RowDefinition Height="50"/>
                                <RowDefinition Height="2"/>
                            </Grid.RowDefinitions>
                            <Grid HeightRequest="50">
                                <Label Text="Non-veg Pizza" VerticalTextAlignment="Center" Margin="10,0,0,0"/>
                                <Image Margin="10" HorizontalOptions="End" HeightRequest="15" WidthRequest="15" Source="{Binding IsExpanded,Source={x:Reference expander2},Converter={StaticResource ExpanderIconConverter}}"/>
                            </Grid>
                            <BoxView Grid.Row="1" IsVisible="{Binding Path=IsExpanded, Source={x:Reference expander2}, Converter={StaticResource SeperatorVisibilityConverter}, ConverterParameter='Header'}" BackgroundColor="Green"/>
                        </Grid>
                    </syncfusion:SfExpander.Header>
                    <syncfusion:SfExpander.Content>
                        <Grid BackgroundColor="#FFFFFF">
                            <Grid.RowDefinitions>
                                <RowDefinition Height="Auto"/>
                                <RowDefinition Height="2"/>
                            </Grid.RowDefinitions>
                            <Label Text="Non-veg pizza is prepared by including the meat and animal tissue products." HeightRequest="50" TextColor="#303030" Margin="10,10,10,10" VerticalTextAlignment="Center"/>
                            <BoxView Grid.Row="1" IsVisible="{Binding Path=IsExpanded, Source={x:Reference expander2}, Converter={StaticResource SeperatorVisibilityConverter}, ConverterParameter='Content'}" BackgroundColor="Green"/>
                        </Grid>
                    </syncfusion:SfExpander.Content>
                </syncfusion:SfExpander>
            </StackLayout>
        </ScrollView>
    </ContentPage.Content>

</ContentPage>
 ```

**C#**

Converter used to show or hide the separator line based on the [IsExpanded](https://help.syncfusion.com/cr/maui/Syncfusion.maui.Expander.SfExpander.html#Syncfusion_Maui_Expander_SfExpander_IsExpanded) property.

 ```c#
    public class ExpanderIconConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
    {
        if ((bool)value)
        {
            return ImageSource.FromFile("arrow_down.png");
        }
        else
        {
            return ImageSource.FromFile("arrow_up.png");
        }
    }

    public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture)
    {
        throw new NotImplementedException();
    }
}
 ```

Download the complete sample from [GitHub](https://github.com/SyncfusionExamples/How-to-show-separator-for-.NET-MAUI-SfExpander)
