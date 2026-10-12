# Drone Vision Safety Check

A proof-of-concept website for a drone camera image model trained in Google Teachable Machine. The model sorts what the camera sees into two classes:

- **Danger**: obstacles (trees, power lines) and unpredictable activity (a backflip on a bike). The drone should stop or steer away.
- **Safe**: clear space and normal activity (a person walking). The drone can continue.

The page runs the model in the browser with TensorFlow.js. You can use the live camera or upload a photo.

## Files

```
index.html          the website
model/model.json    model structure (exported from Teachable Machine)
model/metadata.json class labels
model/weights.bin   trained weights
samples/            sample photos visitors can click to test the model
```

## Adding sample photos

Open the `samples` folder in the repository, click **Add file → Upload files**, and drag in your photos. They show up in the website's "Sample photos" section automatically, with the file name as the caption (`power-line-1.jpg` becomes "power line 1").

## Publish on GitHub Pages

1. Create a new **public** repository on github.com, for example `drone-vision`.
2. Click **Add file → Upload files** and drag in `index.html`, `README.md` and the whole `model` folder. Then click **Commit changes**.
3. Go to **Settings → Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, choose branch **main** and folder **/(root)**, then click **Save**.
4. Wait a minute or two, then refresh the page. Your site address appears at the top, for example `https://YOUR-USERNAME.github.io/drone-vision/`.

GitHub Pages uses HTTPS, so the camera works there. When the browser asks, click **Allow** for camera access.

## Limitation

The model classifies the whole frame. It doesn't locate the obstacle or measure its distance, so a real drone would also need object detection and depth or distance sensors.
