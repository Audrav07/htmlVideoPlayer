# Custom Video Player

## Objective:
When the HTML page is loaded in a browser, it displays a video player with controls for playing/pausing the video, scrolling through the video progress, skipping/ rewinding, changing the volume, and adjusting the playback speed. None of these controls currently work. Write the necessary JavaScript code to bring functionality to this page.

## Steps:

- Buttons:
	* Play
	* Pause
	* Skip 
	* Volume Slider
	* Speed Slider

``function togglePlay(){
	const method = video.paused ? 'play' : 'pause';
	video[method]();
}``

``function updateButton() {
  const icon = this.paused ? '►' : '❚ ❚';
  console.log(icon);
  toggle.textContent = icon;
}``

``function skip(){
	video.currentTime += parseFloat(this.dataset.skip);
}``

``function handleRangeUpdate(){
	video[this.name] = this.value;
}``

``function handleProgress(){
	const percent = (video.currentTime / video.duration) * 100;
	progressBar.style.flexBasis = `${percent}%`;
}``

``function scrub(e){
	const scrubTime = (e.offsetX / progress.offsetWidth) * video.duration;
	video.currentTime = scrubTime;
}``

## Event Listeners for the buttons
  ```video.addEventListener('click', togglePlay);
video.addEventListener('play', updateButton);
video.addEventListener('pause', updateButton);
video.addEventListener('timeupdate', handleProgress)
``
``
``
``
``toggle.addEventListener('click', togglePlay);
skipButtons.forEach(button => button.addEventListener('click', skip));
ranges.forEach(range => range.addEventListener('change', handleRangeUpdate));
ranges.forEach(range => range.addEventListener('mousemove', handleRangeUpdate));``

``let mousedown = false;``

``progress.addEventListener('click', scrub);
progress.addEventListener('mousemove', (e) => mousedown && scrub(e));
progress.addEventListener('mousedown', () => mousedown = true);
progress.addEventListener('mouseup', () => mousedown = false);``
