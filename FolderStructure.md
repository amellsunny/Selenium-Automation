# Folder Structure with Files

TMO_UI_Test
│
├── src
│   ├── main
│   │   ├── java
│   │   │   ├── com.tmo.ui.pages
│   │   │   │   ├── HomePage.java
│   │   │   │   └── ShopPage.java
│   │   │   ├── com.tmo.ui.utils
│   │   │   │   ├── ExcelUtils.java
│   │   │   │   └── ConfigReader.java
│   │   │   └── ...
│   │
│   ├── test
│   │   ├── java
│   │   │   ├── com.tmo.ui.tests
│   │   │   │   ├── BaseTest.java   
│   │   │   │   ├── HomePageTest.java
│   │   │   │   ├── ShopPageTest.java
│   │   │   │   └── 
│   │   │   └── ...
│   │   └── resources
│   │       ├── TestData.xlsx
│   │       ├── config.properties
│   │       └── ...
├── pom.xml
└── ...
