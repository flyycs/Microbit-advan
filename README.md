# Coolguy_advan_extension

Coolguy-advanced-extension for Makecode. It's micro:bit extension board, which include basic and advanced functionalities like battery module, two DC motor drivers and 5V IO interfaces. What's more the inteface is RJ11 based, it's easy to plug and use by students and teachers. It can plug Wifi, Camera and and etc, see below for detail. 

## Feature

- Onboard battery source (powered by 3.7V rechargeable battery)
- Drive two motors simultaneously (motor interface A and B)
- Two IIC communication interfaces (serial interface A and B)
- Three dual IO interfaces（interface P1, P2, and P16）
- A multiplexing IO interface（interface P0）

## Link to product page

http://www.coolguymaker.com/uploads/download/20201208/1318331361b0545.pdf

## Hardware Preview

- ### front

![Product](https://user-images.githubusercontent.com/34023728/99958245-007d8c80-2dc4-11eb-9b37-dc60b6a1a5b9.png)

![back view](https://user-images.githubusercontent.com/34023728/99958253-02dfe680-2dc4-11eb-87b9-5b9311b31110.png)

## Blocks Preview

### Camera

The camera can detect faces, specific cards, moving objects, as well as recognize faces saved in advance. The sample for the camera to detect the card and display the result is shown below.

```typescript
Coolguy_advan.VisionSensor_Begin(exter_ports2.J5, VisionSensor_Mode.CARD)
basic.forever(function () {
    if (Coolguy_advan.VisionSensor_Detected(VisionDetect_Card.Card_Squar)) {
        basic.showIcon(IconNames.Yes)
    } else {
        basic.showIcon(IconNames.No)
    }
})
```

### WIFI

Same as other blocks, when using the WIFI module, you need to select the connected interface and set the account password (just the first time you use it), and then you can read the string from the cloud service or read it from the cloud service.

```typescript
Coolguy_advan.iCloudMemory_Serial_Init(exter_ports2.J5)
Coolguy_advan.iCloudMemory_WiFi_SSIDPWD_Config("CoolGuyRobot", "robotrobot")
basic.forever(function () {
    basic.showString(serial.readLine())
})
```

### AI

The internet is necessary when AI module works. The working mode should be set after initialization (as shown below). The AI module supports voice dialogue, voice recognition and voice conversion.

```typescript
Coolguy_advan.SoundSensor_SetPort(exter_ports2.J5)
Coolguy_advan.SoundSensor_SetWiFi("CoolGuyRobot", "robotrobot")
Coolguy_advan.SoundSensor_WaitInit()
Coolguy_advan.SoundSensor_SetMode(SoundSensor_Mode.MODE_ASR)
basic.showIcon(IconNames.Heart)
```

### Multi-channel Voice Recorder

Multi-channel voice recorder can record and play sounds in channels 1-6 respectively. An example is as follows, record and play the voice on channel 1, and the duration is set by `pasue`.

```typescript
input.onButtonPressed(Button.A, function () {
    Coolguy_advan.wtr050_recordstart(1)
    basic.pause(5000)
    Coolguy_advan.wtr050_recordstop()
})
input.onButtonPressed(Button.B, function () {
    Coolguy_advan.wtr050_playvoice(1)
    basic.pause(5000)
    Coolguy_advan.wtr050_stopvoice()
})
Coolguy_advan.wtr050_Init(exter_ports3.J1)
```

## License

MIT

## Supported targets

* for PXT/microbit (The metadata above is needed for package search.)

