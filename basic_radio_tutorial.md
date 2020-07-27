# basic_radio_tutorial
### @explicitHints true

## Step 1

Pick you radio ``||radio:channel||``

#### ~ tutorialhint
When should you set your radio channel? 
```blocks
radio.setGroup(24)
```

## Step 2
Pick ``||input: a button||`` to ``||radio:send||`` a number over the radio.

#### ~ tutorialhint
This sends the number 9 when button A is pressed.
```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(9)
})
```

## Step 3
``||basic:Show||`` an icon when the radio ``||radio:receives a number||``.
#### ~ tutorialhint
This shows a happy face whenever the micro:bit receives a number over radio.
```blocks
radio.onReceivedNumber(function (receivedNumber) {
    basic.showIcon(IconNames.Happy)
})
```

## Step 4
`|Download|` the code and try it out.
#### ~ tutorialhint
This is a potential solution.
```blocks
radio.setGroup(24)
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(9)
})
radio.onReceivedNumber(function (receivedNumber) {
    basic.showIcon(IconNames.Happy)
})
```