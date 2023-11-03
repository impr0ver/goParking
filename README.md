# goparking
This project is taken from https://github.com/LdDl/goparking.git.
Thank you "LdDl" for a wonderful project. The project has been modified due to new versions of the opencv and gocv libraries. In some places in the code, type casting was performed. The function of creating a photo from the camera based on an event has also been added.
A bug has also been identified where the "WaitKey" function will cause the application to panic. The error is related to running this function inside the goroutine (for mac users).

## Installation
As it uses GoCV, first of all you have to install it. Please see steps described here https://gocv.io/getting-started/.</br>
If you successfully installed everything (GoCV, OpenCV, OpenCV-contrib), then you good to go. 


- Configuration</br>
Open example.json file in main project folder and edit fields to fit your needs.
```js
{
  // videoType - type of input. It can be either local file or web-service ("url") or connected camera to your PC ("device")
  "videoType": "url",
  // videoSource - link to your video. If your videoType is "device", then just provide number of that device: for example "0"
  "videoSource": "/results/parking.mp4",
  // imageResizing - parameter to scale your image (for fast proccessing or other needs). In example it is same as input.
  "imageResizing": [
    854,
    480
  ],
  // showImage - display image or not
  "showImage": true,
  // laplacian - parameter for Laplace Operator (https://en.wikipedia.org/wiki/Laplace_operator)
  // Please see https://docs.opencv.org/3.4.0/d5/db5/tutorial_laplace_operator.html
  // While playng with "imageResizing" you have to change this parameter too to get good results.
  "laplacian": 2.0,
  // areas - array of parking lots.
  // each area has ID (string) and set of coordinates.
  // There are no setMouseCallback() in GoCV package (see https://github.com/hybridgroup/gocv/issues/211), 
  // so I can not implement good "GUI" for extracting clicked points on image.
  // For extracting needed points you need to use some 3-d party applications like Paint (Windows) or KolourPaint (Linux).
  "areas": [
    {
      "id": "1t_lot",
      "coords": [
        [
          368,
          329
        ],
        [
          410,
          328
        ],
        [
          437,
          350
        ],
        [
          387,
          353
        ]
      ]
    }
  ]
}
```

- Run</br>
For Linux, Windows, Mac:
```cmd
./main
```

## Thanks
Big thanks to creator 
