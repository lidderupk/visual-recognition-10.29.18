# Online Meetup: Introduction to Visual Recognition

This is a good starting point if you are new to IBM Cloud and Watson Visual Recognition. IBM offers multiple paths into the Visual Recognition space depending on your experience. This online workshop is designed for beginners and intermediate programmers.

```
Upkar Lidder, IBM Developer Advocate (@lidderupk)
Upkar Lidder is a Full Stack Developer and Data Wrangler with strong experience in NodeJS and Python. His current passions include enjoying various kinds of ramen, hiking, tennis and learning the magic behind ML. He is always up for a chat over good coffee and/or beer.
```

## Links
1. [IBM Cloud sign up](https://ibm.biz/BdYbR8)
2. [Watson Visual Recognition API](https://console.bluemix.net/apidocs/visual-recognition)
3. [Watson Visual Recognition Docs](https://console.bluemix.net/docs/services/visual-recognition/getting-started.html#getting-started-tutorial)
4. [Watson Visual Recognition Starter Kit](https://console.bluemix.net/developer/watson/starter-kits/watson-visual-recognition-basic)
4. [Tutorial on Creating a Custom Classifier](https://www.youtube.com/watch?v=7gVVJnNZw5o)
6. [Watson API SDKs](https://github.com/watson-developer-cloud)
7. [Slides for this talk](assets/ibm-watson-visual-api.pdf)

## Curl Examples

### Built in models
1. Classify an [image using URL](https://github.com/lidderupk/watson-visual-galvanize-08.25.18/blob/master/assets/sf-cable-car.jpg).

    ```
    curl -u "apikey:$watson_visual_key" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://github.com/lidderupk/watson-visual-galvanize-08.25.18/blob/master/assets/sf-cable-car.jpg?raw=true&version=2018-03-19"
    ```

2. Single local image

    ```
    curl -X POST -u "apikey:$watson_visual_key" -F "images_file=@$watson_visual_directory_root/kids.jpg" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```

3. Multiple local images - zip file

    ```
    curl -X POST -u "apikey:$watson_visual_key" -F "images_file=@$watson_visual_directory_root/multiple_images.zip" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```

4. Face model

    ```
    curl -X POST -u "apikey:$watson_visual_key" -F "images_file=@$watson_visual_directory_root/kids.jpg" -F "threshold=0.6" "https://gateway.watsonplatform.net/visual-recognition/api/v3/detect_faces?version=2018-03-19"
    ```

5. Food model

    ```
    curl -X POST -u "apikey:$watson_visual_key" -F "images_file=@$watson_visual_directory_root/fruitbowl.jpg" -F "classifier_ids=food" -F "threshold=0.6" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
### Custom models
6. Get all classifiers

    ```
    curl -u "apikey:$watson_visual_key" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?verbose=true&version=2018-03-19"
    ```

7. Use the default model

    ```
    curl -X POST -u "apikey:$watson_visual_key" -F "images_file=@$watson_visual_directory_root/galvanize-07.24.18/gsk-hackathon-images/test/mucinex-1.JPG" -F "threshold=0.6" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```

8. Use custom model

    ```
    curl -X POST -u "apikey:$watson_visual_key" -F "images_file=@$watson_visual_directory_root/galvanize-07.24.18/gsk-hackathon-images/test/mucinex-1.JPG" -F "classifier_ids=medicinexcustomxupkar_1628839369" -F "threshold=0" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
