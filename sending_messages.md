# sending_messages
### @explicitHints true

## Step 1

Pick you radio ``||radio:channel||``

#### ~ tutorialhint
When should you set your radio channel? 
```blocks
radio.setGroup(24)
```

## Step 2
Pick some ``||input: actions||`` that will ``||radio:send||`` some numbers over the radio.

#### ~ tutorialhint
This sends the number 9 when button A is pressed and 18 when button B is pressed.
```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(9)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(18)
})
```

## Step 3
``||basic:Show||`` different icons depending on what number the radio ``||radio:receives||``.
#### ~ tutorialhint
We use an if/else if block to ask questions about the number received. To get the else if block, press the + button on the if/else block. This shows a small heart if a 9 is received and a big heart if 18 is received.
```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 9) {
        basic.showIcon(IconNames.SmallHeart)
    } else if (receivedNumber == 18) {
        basic.showIcon(IconNames.Heart)
    }
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
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(18)
})


radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 9) {
        basic.showIcon(IconNames.SmallHeart)
    } else if (receivedNumber == 18) {
        basic.showIcon(IconNames.Heart)
    }
})
```