# 📚 Tomcat + Maven Q&A Cheat Sheet

---

## ❓ 1) What does `mvn clean package` do?

✅ It:
- **Cleans**: Deletes the old `/target` build directory.
- **Packages**: Compiles your source code & packages it as a `JAR` or `WAR` depending on `<packaging>` in `pom.xml`.

Example:
```
mvn clean package
👉 Creates:
target/myapp.jar (for a JAR)
target/mywebapp.war (for a WAR)
```

---

## ❓ 2) What does `java -cp target/simple-maven-app-1.0-SNAPSHOT.jar com.example.App` do?
✅ It runs a class (`com.example.App`) from your built JAR using the classpath option `-cp`.
- `-cp` means "use this JAR or folder for classes"
- `com.example.App` is your main class with `public static void main`

---

## ❓ 3) How did we change the project from JAR to WAR?
✅ Changes in `pom.xml`:

| Aspect             | JAR                     | WAR                     |
|--------------------|-------------------------|-------------------------|
| `<packaging>`      | jar (or default)        | war                     |
| Dependencies       | No servlet API          | ✅ Added javax.servlet-api |
| Plugins            | maven-compiler-plugin   | ✅ Added maven-war-plugin |

👉 This tells Maven to create a deployable web application for servlet containers like Tomcat.

---

## ❓ 4) Why do we install Tomcat using wget?
✅ Using wget:
- Downloads the official Tomcat `.tar.gz` manually
- No dependency on OS package manager (apt, yum)
- Useful for:
  - Using specific Tomcat versions
  - Full control over installation location

---

## ❓ 5) Why do we extract Tomcat to /opt/tomcat?
✅ By Linux convention:

| Folder       | Usage                     |
|--------------|---------------------------|
| /usr/bin     | System-managed apps       |
| /usr/local   | Locally compiled apps     |
| /opt         | Manually installed apps   |

Putting Tomcat in `/opt/tomcat`:
- Keeps server clean & organized
- Follows best practices
- Easier to manage multiple versions

---

## ❓ 6) Would Tomcat work if extracted elsewhere?
✅ Yes - Tomcat is just a folder with scripts. You could run from:
- `/home/youruser/tomcat`
- `/usr/local/tomcat`
- `/tmp/tomcat` (not recommended)

But `/opt/tomcat` is standard for clarity & maintainability.

---

## ❓ 7) Why does `sudo cd` not work?
✅ Because:
- `cd` is a shell built-in, not a separate program
- `sudo` runs programs, not built-ins

✅ Correct ways:
```
# Option 1:
cd /opt/tomcat/bin
sudo ./startup.sh

# Option 2:
sudo -i  # Open root shell
cd /opt/tomcat/bin
./startup.sh
```

---

## ❓ 8) How did we make Tomcat .sh files executable?
✅ We ran:
```
sudo find /opt/tomcat/bin/ -name "*.sh" -exec chmod +x {} \;
```
This ensures all shell scripts in `bin/` are executable.

---

## ✅ Summary

| Tool    | Installation Method       |
|---------|---------------------------|
| Maven   | Package manager (apt)     |
| Tomcat  | Manual download + unpack  |

| Project Type | Build Artifact | How to Run               |
|--------------|----------------|--------------------------|
| JAR          | .jar           | `java -jar` or `java -cp` |
| WAR          | .war           | Deploy to Tomcat         |

---

## ✅ To run Tomcat manually
```
sudo -u tomcat /opt/tomcat/bin/startup.sh
```
Open in browser: `http://<your-server-ip>:8080`

🚀 **Tip**: Use a systemd service for auto-start  
Ask: *"Show me the Tomcat systemd service file!"* for background service setup.

---

## 📌 How to use this
✅ Copy this Markdown into:
- `README.md`
- Personal notes
- GitHub wiki

✅ It covers:
- `mvn` basics
- WAR vs JAR differences
- Manual Tomcat installation
- Linux best practices

---

✨ **Done! Happy deploying!**  
🚀 *Say "Show me!" for:*
- `systemd` unit file example
- Minimal `web.xml` & JSP example
- Ready-to-deploy WAR template
```

This markdown includes:
1. Properly formatted headers and sections
2. Code blocks with syntax highlighting
3. Comparison tables
4. Command examples with outputs
5. Organized Q&A structure
6. Clear visual separation of concepts
7. Emojis and icons for visual scanning
8. Practical usage notes at the end

You can directly copy-paste this into any Markdown-supported platform like GitHub, Notion, or Obsidian.
