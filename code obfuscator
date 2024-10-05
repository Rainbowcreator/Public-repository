package com.example.myproject;

public class MyClass {
    /*
     * © Rainbowcreator, 2024-2026
     * All rights reserved.
     */
    private int myVariable;
    // 类的其他内容
}
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import java.util.Random;

public class CodeObfuscator {

    private Map<String, String> variableRenamingMap = new HashMap<>();
    private Map<String, String> methodRenamingMap = new HashMap<>();
    private Random random = new Random();

    public void obfuscate(String sourceFilePath, String destinationFilePath) {
        try (BufferedReader reader = new BufferedReader(new FileReader(new File(sourceFilePath)));
             BufferedWriter writer = new BufferedWriter(new FileWriter(new File(destinationFilePath)))) {

            String line;
            while ((line = reader.readLine())!= null) {
                String obfuscatedLine = obfuscateLine(line);
                writer.write(obfuscatedLine + "\n");
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private String obfuscateLine(String line) {
        StringBuilder obfuscatedLine = new StringBuilder();
        String[] words = line.split("\\s+");
        for (String word : words) {
            if (isVariable(word)) {
                word = obfuscateVariable(word);
            } else if (isMethod(word)) {
                word = obfuscateMethod(word);
            }
            obfuscatedLine.append(word).append(" ");
        }
        return obfuscatedLine.toString().trim();
    }

    private boolean isVariable(String word) {
        // 更准确的判断变量的逻辑，例如检查常见的变量命名模式
        return word.matches("[a-zA-Z_][a-zA-Z0-9_]*");
    }

    private boolean isMethod(String word) {
        // 更准确的判断方法的逻辑，例如检查是否后跟括号
        return word.matches("[a-zA-Z_][a-zA-Z0-9_]*\\(.*\\)");
    }

    private String obfuscateVariable(String variableName) {
        if (!variableRenamingMap.containsKey(variableName)) {
            String newName = generateRandomName();
            variableRenamingMap.put(variableName, newName);
        }
        return variableRenamingMap.get(variableName);
    }

    private String obfuscateMethod(String methodName) {
        if (!methodRenamingMap.containsKey(methodName)) {
            String newName = generateRandomName();
            methodRenamingMap.put(methodName, newName);
        }
        return methodRenamingMap.get(methodName);
    }

    private String generateRandomName() {
        StringBuilder name = new StringBuilder();
        int length = random.nextInt(15) + 5;  // 增加随机名称的长度范围
        for (int i = 0; i < length; i++) {
            char c = (char) (random.nextInt(26) + 'a');
            name.append(c);
        }
        return name.toString();
    }

    public static void main(String[] args) {
        CodeObfuscator obfuscator = new CodeObfuscator();
        obfuscator.obfuscate("yourSourceCode.java", "obfuscatedCode.java");
    }
}
