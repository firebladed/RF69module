# RF69module
Simple PCB for HopeRF RFM69HCW exposing SPI interface and DIO to access via SPI Bus

- RFM69HCW SPI interface accessable on Chip Select 0
- RFM69HCW DIO accessable via MCP23S08 IO expander on  Chip Select 1

- NO internal Antenna
- Antenna Attached Via Microcoaxial RF Connector

## Pin Connections 
1. \~ALERT\~
2. GND
3. SPI_MISO
4. SPI_MOSI
6. SPI_SCLK
7. SPI_CS0
8. SPI_CS1
9. GND
10. 3V3

## Device Tree

### RFM69HCW
TODO

### MCP23S08
IO expander configured using [mcp23s08_spi](https://github.com/torvalds/linux/blob/master/drivers/pinctrl/pinctrl-mcp23s08_spi.c) linux kernel driver

e.g
```
gpiom1: gpio@0 {
        compatible = "microchip,mcp23s08";
        gpio-controller;
        #gpio-cells = <2>;
        microchip,spi-present-mask = <0x01>;
        reg = <0>;
        spi-max-frequency = <1000000>;
        interrupt-parent = <&gpio1>;
        interrupts = <8 IRQ_TYPE_LEVEL_LOW>;
        interrupt-controller;
        drive-open-drain;

```

[mcp23s08 Driver Device Tree Documentation](https://github.com/torvalds/linux/blob/master/Documentation/devicetree/bindings/pinctrl/pinctrl-mcp23s08.txt)

