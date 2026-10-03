# Norna Converter - FFmpegKit LGPL for iOS

This repository contains the GitHub Actions workflow to build `FFmpegKitNext` v8.1.1 (the official successor to `ffmpeg-kit`) specifically for iOS, conforming strictly to the LGPL-3.0 license.

## Why this repository?

The `ffmpeg-kit-react-native` community fork (`ffmpegkit-maintained`) provides an updated 8.1 LTS build for Android (`dev.ffmpegkit-maintained:ffmpeg-kit-full:8.1.9`) but it does **not** provide prebuilt iOS frameworks (CocoaPods).

To upgrade iOS from the deprecated 2023 version (6.0) to the 8.1 LTS version while maintaining LGPL compliance, we must compile it ourselves.

## Built-in Encoders

This build includes the following LGPL/BSD compatible external libraries:
- `lame` (MP3)
- `opus`
- `libvorbis` (OGG)
- `libvpx` (WebM)
- `dav1d` (AV1 decoder)
- `libwebp` (WebP)
- `kvazaar` (HEVC/H.265 software fallback)
- `openh264` (H.264 software fallback)
- `videotoolbox` (Hardware Accelerated H.264 / HEVC)
- `audiotoolbox` (Hardware Accelerated AAC / ALAC)

It **DOES NOT** include `libx264` or `libx265`, meaning it is completely GPL-free. Strict LGPL compliance is maintained (zimg and soxr have been removed).

## How to use

1. Go to the **Actions** tab of this repository.
2. Run the **Build FFmpegKit LGPL for iOS** workflow.
3. The workflow will take a while to compile everything on a macOS runner.
4. Once completed, download the `ffmpeg-kit-ios-full-lgpl` artifact zip.
5. Create a GitHub Release in this repository (e.g., `8.1.1-1`) and attach the `.zip` file.
6. Create an `ffmpeg-kit-ios-full-lgpl.podspec` referencing the download URL of your newly created release.
