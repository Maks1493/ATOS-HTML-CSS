# ATOS-HTML-CSS
const fs = require("fs");

function updateVersionInFile(filePath) {
  fs.readFile(filePath, "utf8", (err, data) => {
    if (err) return console.error("Error reading file:", err);

    try {
      const jsonData = JSON.parse(data);
      jsonData.version = "1.0.0";
      fs.writeFile(
        filePath,
        JSON.stringify(jsonData, null, 2),
        "utf8",
        (err) => {
          if (err) return console.error("Error writing file:", err);
          console.log("File updated successfully!");
        }
      );
    } catch (parseError) {
      console.error("Error parsing JSON:", parseError);
    }
  });
}

// Usage example
updateVersionInFile("package.json"); // Update with the actual file path
