# Building a Data Display with Blocks
### @explicitHints true

## Step 1
This it the blank template for building the data display. A few things have been
initialized for you, but feel free to change them.

```template
let StripLEDs: neopixel.Strip = null
let GatorLEDS: neopixel.Strip = null
gatorEnvironment.beginEnvironment()
GatorLEDS = neopixel.create(DigitalPin.P12, 5, NeoPixelMode.RGB)
StripLEDs = neopixel.create(DigitalPin.P1, 60, NeoPixelMode.RGB)
GatorLEDS.setBrightness(20)
StripLEDs.setBrightness(100)
basic.showNumber(Math.round(gatorEnvironment.getMeasurement(measurementType.degreesF)))

input.onButtonPressed(Button.A, function () {
    basic.showString("Sound")
    for (let index = 0; index < 4; index++) {
        GatorLEDS.showBarGraph(gatorMicrophone.getSoundIntensity(), 2047)
        StripLEDs.showBarGraph(gatorMicrophone.getSoundIntensity(), 2047)
        basic.pause(2000)
        GatorLEDS.showColor(neopixel.colors(NeoPixelColors.Indigo))
        StripLEDs.showColor(neopixel.colors(NeoPixelColors.Indigo))
        basic.pause(2000)
        GatorLEDS.clear()
        StripLEDs.clear()
        basic.pause(2000)
        GatorLEDS.setPixelColor(0, neopixel.colors(NeoPixelColors.Yellow))
        StripLEDs.setPixelColor(10, neopixel.colors(NeoPixelColors.Yellow))
        GatorLEDS.show()
        StripLEDs.show()
        basic.pause(2000)
    }
})
input.onButtonPressed(Button.AB, function () {
    basic.showString("Soil Moisture")
    for (let index = 0; index < 4; index++) {
        if (gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P8) * 100 < 40) {
            music.playTone(262, music.beat(BeatFraction.Whole))
            music.playMelody("E B C5 A B G A F ", 120)
            music.rest(music.beat(BeatFraction.Whole))
        }
        basic.pause(5000)
    }
})
input.onButtonPressed(Button.B, function () {
    basic.showString("Environmental")
    for (let index = 0; index < 4; index++) {
        led.plotBarGraph(
        gatorEnvironment.getMeasurement(measurementType.humidity),
        100
        )
        basic.pause(5000)
        if (gatorEnvironment.getMeasurement(measurementType.humidity) < 80) {
            basic.showLeds(`
                . # . # .
                . # . # .
                . . . . .
                # . . . #
                . # # # .
                `)
        } else {
            basic.showIcon(IconNames.Sad)
        }
        basic.pause(5000)
        basic.clearScreen()
        basic.pause(1000)
    }
})

```

```package
gatorMicrophone=github:sparkfun/pxt-gator-microphone#v1.0.20
neopixel=github:microsoft/pxt-neopixel#v0.7.3
gatorEnvironment=github:sparkfun/pxt-gator-environment#v1.0.13
gatorSoil=github:sparkfun/pxt-gator-soil#v1.0.3
```










