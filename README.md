# Placing-imagies-in-indesign
// Define the images and their target coordinates
var images = [
    {filePath: "/path/to/image1.jpg", x: 100, y: 200, width: 200, height: 150},
    {filePath: "/path/to/image2.jpg", x: 350, y: 200, width: 200, height: 150},
    {filePath: "/path/to/image3.jpg", x: 600, y: 200, width: 200, height: 150}
];

// Get the active document
var doc = app.activeDocument;

// Loop through the images and place them
for (var i = 0; i < images.length; i++) {
    var image = images[i];

    // Create a rectangle frame for the image
    var rect = doc.pages[0].rectangles.add();

    // Set the size and position of the rectangle
    rect.geometricBounds = [image.y, image.x, image.y + image.height, image.x + image.width];

    // Place the image into the rectangle
    rect.place(File(image.filePath));

    // Fit the image proportionally
    rect.fit(FitOptions.PROPORTIONALLY);
}
