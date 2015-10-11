# Windows IoT SSD1306

this lib allow your Windows IoT app to use your raspberry pi (model b) sith the SPI display SSD1306 made by [Adafruit ssd1306 product][adafruit-ssd1606-product]

This lib is based on 

- my fork of [Windows IoT Samples on gitgub][Microsoft-iot-samples]
- [Adafruit official library for ssd1306 on github][adafruit-ssd1606-official-lib]

the "official" library for SpiDisplay included in [Windows IoT samples on github] [Microsoft-iot-samples] is designed for SSD1306 128x64 device and have some problem on my devide (i've the cheaper 128x32)

# Usage
for use this lib you have to:
 * create a windows universal platform app (for Windows 10)
 * add the reference for Windows IoT extension
 * add the referenc for this project or for the [nuget package for ssd1306][nuget-windows-iot-1306]
 
add this code (for examle)

```cs
    SSD1306 ssd1306 = new SSD1306();
    public  MainPage()
    {
        this.InitializeComponent();
        Unloaded += MainPage_Unloaded;
        InitAll();
    }
    /* Initialize GPIO, SPI, and the display */
    private async void InitAll()
    {
        await ssd1306.InitAll();
        ssd1306.WriteLineDisplayBuf("hello worl"d, 0, 0);
        ssd1306.DisplayUpdate();    /* Write our changes out to the display */
    }
    private void MainPage_Unloaded(object sender, object args)
    {
        /* Cleanup */
        ssd1306.DisposeAll();
    }        
```

 [adafruit-ssd1606-product]: <http://www.adafruit.com/product/661>
 [Microsoft-iot-samples]: <https://github.com/ms-iot/samples>
 [adafruit-ssd1606-official-lib]: <https://github.com/adafruit/Adafruit_SSD1306>
 [nuget-windows-iot-1306]: <https://www.nuget.org/packages/WindowsIot-SPiDisplay-SSD1306/>