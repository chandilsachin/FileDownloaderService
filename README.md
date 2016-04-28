# FileDownloaderService
An Intent service that can be used to download a file in background with progressbar .

# Installation

Copy and paste FileDownloaderService.java file in your project and you are ready to go.

# Uses:
```java
    class imageDownloadReceiver1 extends ResultReceiver
    {

        public imageDownloadReceiver1(Handler handler)
        {
            super(handler);
        }

        @Override
        protected void onReceiveResult(int resultCode, Bundle resultData)
        {
            super.onReceiveResult(resultCode, resultData);
            switch (resultCode)
            {
                case FileDownloaderService.RESPONSE_CODE_DOWNLOAD_RESULT:
                    String outFilePath = resultData
                            .getString(FileDownloaderService.ARGUMENT_TARGET_FILE);
                    if (outFilePath != null)
                    {
                        // outFilePath contains path of downloaded file. Do whatever you want to do with it.
                        System.out.println("Downloaded " + outFilePath);
                    }
                    break;

                default:
                    break;
            }
        }
    }
```

Call intentService like following:
```java
FileDownloaderService.startAction(getContext(), imageUrl, "image path to save image to", new imageDownloadReceiver(new Handler()));
```

This example is to download image. Any file can be downloaded like this.
