# Android_MediaPlayer_Web
Playing Song From Web by URL

This topic is a part of [My Complete Andorid Course](https://github.com/ananddasani/Android_Apps)

# Code

#### MainActivity.java
```
Button playPauseButton;
SeekBar seekBar;

    MediaPlayer mediaPlayer = new MediaPlayer();
        try {
            mediaPlayer.setDataSource("http://djbloom.info/Music/My%20Music/Billy%20Joel/billyjoel_pianoman.mp3");
        } catch (IOException e) {
            e.printStackTrace();
        }

        //set on prepared listener
        mediaPlayer.setOnPreparedListener(new MediaPlayer.OnPreparedListener() {
            @Override
            public void onPrepared(MediaPlayer mp) {
                Toast.makeText(MainActivity.this, "Buffering Music From URL", Toast.LENGTH_SHORT).show();
                mp.start();

                seekBar.setMax(mediaPlayer.getDuration());
                seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
                    @Override
                    public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
                        if (fromUser)
                            mediaPlayer.seekTo(progress);
                    }

                    @Override
                    public void onStartTrackingTouch(SeekBar seekBar) {

                    }

                    @Override
                    public void onStopTrackingTouch(SeekBar seekBar) {

                    }
                });
            }
        });
        mediaPlayer.prepareAsync();

        playPauseButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                // Music is paused then start (initially)
                if (playPauseButton.getText().toString() == "Play") {
                    playPauseButton.setText("Pause");

                    mediaPlayer.start();
                } else {
                    playPauseButton.setText("Play");

                    mediaPlayer.pause();
                }
            }
        });
    }
```

# App Highlight
![Media Player Web Code](https://user-images.githubusercontent.com/74413402/192093090-90857294-07f5-4093-9b7f-551cb2814495.png)

![Media Player Web  App](https://user-images.githubusercontent.com/74413402/192093086-810b57af-c0f9-4e6c-a29d-4db198ebcb0a.png)
