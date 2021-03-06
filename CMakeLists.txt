CMAKE_MINIMUM_REQUIRED(VERSION 3.14)
PROJECT(my-little-video-player C CXX)

SET(CMAKE_CXX_STANDARD 14)
SET(CMAKE_BUILD_TYPE Debug)
SET(CMAKE_CXX_FLAGS "-Wall -Wextra -Wpedantic")
SET(THREADS_PREFER_PTHREAD_FLAG ON)

ADD_SUBDIRECTORY(lib/ffmpeg)
ADD_SUBDIRECTORY(lib/sdl2)
FIND_PACKAGE(Threads)

SET(sources
  src/log.cpp
  src/timer.cpp
  src/demuxer.cpp
  src/decoder.cpp
  src/video_converter.cpp
  src/video_renderer.cpp
  src/audio_resampler.cpp
  src/audio_renderer.cpp
  src/audio_buffer.cpp
  src/task_queue.h
  )

#ADD_EXECUTABLE(log_example example/log_example.cpp ${sources})
#ADD_EXECUTABLE(demuxer_example example/demuxer_example.cpp ${sources})
#ADD_EXECUTABLE(decoder_example example/decoder_example.cpp ${sources})
#ADD_EXECUTABLE(video_converter_example example/video_converter_example.cpp ${sources})
#ADD_EXECUTABLE(video_renderer_example example/video_renderer_example.cpp ${sources})
#ADD_EXECUTABLE(audio_resampler_example example/audio_resampler_example.cpp ${sources})
#ADD_EXECUTABLE(audio_renderer_example example/audio_renderer_example.cpp ${sources})
ADD_EXECUTABLE(video_player src/video_player.cpp ${sources})

#TARGET_LINK_LIBRARIES(log_example ffmpeg sdl2)
#TARGET_LINK_LIBRARIES(demuxer_example ffmpeg sdl2)
#TARGET_LINK_LIBRARIES(decoder_example ffmpeg sdl2)
#TARGET_LINK_LIBRARIES(video_converter_example ffmpeg sdl2)
#TARGET_LINK_LIBRARIES(video_renderer_example ffmpeg sdl2)
#TARGET_LINK_LIBRARIES(audio_resampler_example ffmpeg sdl2)
#TARGET_LINK_LIBRARIES(audio_renderer_example ffmpeg sdl2)
TARGET_LINK_LIBRARIES(video_player ffmpeg sdl2 Threads::Threads)
