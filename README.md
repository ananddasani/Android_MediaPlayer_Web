# Android_MediaPlayer_Web
Playing Song From Web by URL

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

<img src="app_images/Media Player Web Code.png" width="1000" /><br>

<img src="app_images/Media Player Web App.png" width="300" /><br>
