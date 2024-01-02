# ImageExtensionDetector Documentation

## Overview

This project was assigned for Multimedia Systems course in college

Image Extension Detector is a file analysis tool that identifies image types by reading only the file header. It recognize popular formats such as JPEG, TIFF, RAW, PNG, GIF, and BMP. Without relying on file extensions.

## Usage

### Class: `ImageExtensionDetector`

The main class responsible for detecting the image file type.

#### Public Enums

- `FileType`: Enumerates the supported image file types.
  - `JPEG`
  - `TIFF`
  - `RAW`
  - `PNG`
  - `GIF`
  - `BMP`
  - `UNKNOWN`

#### Public Methods

- `static string getFileTypeString(FileType fileType)`: Converts a `FileType` enum value to its corresponding string representation.

- `static FileType getFileType(const string &filepath)`: Reads the file at the specified `filepath` and returns its detected `FileType`.

#### Private Methods

- `static vector<unsigned char> readFile(const string &filepath)`: Reads the contents of the file at the specified `filepath` and returns a vector of unsigned characters.

- Private methods for each supported image type (`isJPEG`, `isTIFF`, `isRAW`, `isPNG`, `isGIF`, `isBMP`) check if the provided data matches the respective image type's header.

- `static FileType getFileType(const vector<unsigned char> &data)`: Determines the image type based on the provided data.

### Sample Usage in `main`

The `main` function demonstrates the usage of the ImageExtensionDetector class.

```cpp
int main() {
    // Specify the file path
    string filepath = R"(E:\Projects\Cpp\ImageExtensionDetector\test\testingFiles\tiff.tiff)";

    // Get the file type
    ImageExtensionDetector::FileType fileType = ImageExtensionDetector::getFileType(filepath);

    // Print the result
    cout << "The file type is: " << ImageExtensionDetector::getFileTypeString(fileType) << '\n';

    return 0;
}
```

This sample shows how to use the program to detect the image file type based on the provided file path and print the result.

## Dependencies

- `iostream`: Input/output stream handling.
- `fstream`: File stream handling.
- `vector`: Dynamic array for storing file data.
- `algorithm`: Used for vector manipulation and comparison.

## Notes

- The program relies on reading file headers for accurate image type detection.
- Ensure that the specified file path is correct and the file exists before running the program.
