# Hello Java Maven - Jenkins Build Demo

## 📌 Objective
Run a simple Java application using Maven in Jenkins as part of CI/CD learning.

---

## 📂 Project Structure
```
hello-java-maven/
│── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java
```

---

## 🛠 Requirements
- Java JDK 8 or 11
- Maven
- Jenkins (local or via Docker)
- Git (optional)

---

## 📜 Steps to Run

### 1️⃣ Create Project Structure
```bash
mkdir -p hello-java-maven/src/main/java
cd hello-java-maven
```

### 2️⃣ Create Java File
Create `src/main/java/HelloWorld.java`:
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
```

### 3️⃣ Create `pom.xml` in Project Root
```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>hello</artifactId>
    <version>1.0</version>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

### 4️⃣ Start Jenkins
```bash
docker run -p 8080:8080 jenkins/jenkins:lts
```

### 5️⃣ Configure Maven in Jenkins
- Go to **Manage Jenkins → Global Tool Configuration**
- Add Maven installation (e.g., Maven 3.8.6) and check "Install automatically"

### 6️⃣ Create Jenkins Freestyle Job
- Add SCM repo or use local file path
- Build step → Invoke top-level Maven targets
- Select the Maven installation you configured
- Goal: `clean package`
- Save and build

### 7️⃣ Verify Build
- Click **Build Now**
- Open **Console Output**
- You should see:
```
BUILD SUCCESS
```

### 8️⃣ Add Screenshot of Jenkins Build Success

### Jenkins Build Success Screenshot
<img width="1090" height="711" alt="image" src="https://github.com/user-attachments/assets/3f8c4718-2738-4f21-b0ba-1e3dff44ea55" />
