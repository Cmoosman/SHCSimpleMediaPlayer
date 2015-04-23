# SHCSimpleMediaPlayer

`SHCSimpleMediaPlayer` is a simple wrapper around the `AVPlayer` for a use with iOS or OSX.

## Properties
- `@property (nonatomic, readonly) AVPlayer *player;` // `AVPlayer` instance that wrapper is using
- `@property (nonatomic, readonly, assign) NSTimeInterval duration;`  // Duration of the audio asset or value < 0 if duration cannot be determined
- `@property (nonatomic, readonly, assign) NSTimeInterval currentTime;`   //Current position of the playing asset
- `@property (nonatomic, strong) AVPlayerItem *playerItem;` // `AVPlayerItem` currently used by `player`
- `@property (nonatomic, copy) NSURL *assetURL;` // URL of the asset, setting this property causes creating a new `playerItem`
- `@property (nonatomic, readonly) BOOL isPlaying;` // Indication of play/pause state
- `@property (nonatomic, readonly) BOOL isSeekingStatusAvailable;`  // Allow to determine an availability of isSeeking property
- `@property (nonatomic, readonly) BOOL isSeeking;` // Indication of seeking in progress, remark: If isSeekingAvailable==`NO`, value of this property is always `NO`
- `@property (nonatomic, assign) NSTimeInterval playbackBlockInterval;` // How frequent update playback status.
 Defaults to 1.0 second, setting 0.0 prevents the playbackBlock from running

- `@property (nonatomic, copy) SHCAudioPlayerDidPlayToEndBlock   didPlayToEndBlock;` // Block to call at the end of media playback.
- `@property (nonatomic, copy) SHCAudioPlayerPlaybackBlock       playbackBlock;`  // Block called during playback.
- `@property (nonatomic, copy) SHCAudioPlayerDidSetDurationBlock didSetDurationBlock;` // Block called when media asset's duration is known (important for remote URLs). Can be not called at all in case of duration cannot be obtained
- `@property (nonatomic, copy) SHCAudioPlayerHandleErrorBlock    handleErrorBlock;` // Block called in case of error occurrence.

##### Remarks:
All block callbacks are called on the main queue.

## Methods

* `- (void)play;` // Start playback
* `- (void)pause;` // Pause playback
* `- (void)seekToTime:(NSTimeInterval)time;` // Rewind playback to a desired time

