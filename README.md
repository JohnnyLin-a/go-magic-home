# Magic Home Lib

This library offers the possibility to control Magic Home (Magic Hue) LED Strip Controller.  
It is written in [Go](https://golang.org/).

## Features

- Change the state of the LED Strip Controller to on or off
- Change the color of the LED Strip Controller with RGBW
- Request the current state ot the LED Strip Controller

## Library

### Install

```bash
$ go get -u github.com/johnnylin-a/magic-home
```

### Usage

```go
// Create a new Magic Home LED Strip Controller
controller, _ := magichome.New(net.ParseIP("192.168.1.42"), 5577)

// Turn LED Strip Controller on
controller.SetState(magichome.On)

// Tun LED Strip Controller off
controller.SetState(magichome.Off)

// Set color of LED Strip to white
controller.SetColor(magichome.Color{
  R: 255,
  G: 255,
  B: 255,
  W: 0,
})

// Get the current state of the device
// The response looks like
// {
//   "DeviceType": 51,
//   "State": 1,
//   "LedVersionNumber": 6,
//   "Mode": 97,
//   "Slowness": 15,
//   "Color": {
//     "R": 21,
//     "G": 77,
//     "B": 70,
//     "W": 0
//   }
// }
deviceState, _ := controller.GetDeviceState()

// Don't forget to close the connection to the LED Strip Controller
controller.Close()
```


## License

magic-home is released under the [MIT license](LICENSE).
