# Reading Notes 39 -- Analytics and Text-To-Speech

## Amazon Pinpoint

- [Amazon Pinpoint](https://aws.amazon.com/pinpoint/)

Pinpoint is an Amazon communications service for marketing. Pinpoint can handle email, SMS, push and can run campaigns. In addition to the marketing and messaging solutions Pinpoint also handles analytics for mobile and web apps to collect usage metrics.

## Amazon Polly

- [Amazon Polly](https://docs.aws.amazon.com/polly/latest/dg/what-is.html)

Amazon Polly is a hight quality text to speech service. The service model is pay per use for the text synthesis. Previously synthesized speech can be saved for free replays. The advantage of a cloud based solution for hight quality TTS is less power usage and device requirements but this comes at a price.

Example of playback code after initialization from the Polly docs:

```java
// Use MediaPlayer: https://developer.android.com/guide/topics/media/mediaplayer.html

// Create a media player to play the synthesized audio stream.
MediaPlayer mediaPlayer = new MediaPlayer();
mediaPlayer.setAudioStreamType(AudioManager.STREAM_MUSIC);

try {
    // Set media player's data source to previously obtained URL.
    mediaPlayer.setDataSource(presignedSynthesizeSpeechUrl.toString());
} catch (IOException e) {
    Log.e(TAG, "Unable to set data source for the media player! " + e.getMessage());
}

// Prepare the MediaPlayer asynchronously (since the data source is a network stream).
mediaPlayer.prepareAsync();

// Set the callback to start the MediaPlayer when it's prepared.
mediaPlayer.setOnPreparedListener(new MediaPlayer.OnPreparedListener() {
    @Override
    public void onPrepared(MediaPlayer mp) {
        mp.start();
    }
});

// Set the callback to release the MediaPlayer after playback is completed.
mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
    @Override
    public void onCompletion(MediaPlayer mp) {
	mp.release();
    }
});
```
