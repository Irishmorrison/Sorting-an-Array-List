# Sorting-an-Array-List
This program is designed to manage a collection of student objects using an 'ArrayList'. 

Here is the source code:

package Student.java;

public class Student {
    private int rollno;
    private String name;
    private String address;

    public Student(int rollno, String name, String address) {
        this.rollno = rollno;
        this.name = name;
        this.address = address;
    }

    public int getRollno() {
        return rollno;
    }

    public String getName() {
        return name;
    }

    public String getAddress() {
        return address;
    }

    @Override
    public String toString() {
        return "Student{" +
                "rollno=" + rollno +
                ", name='" + name + '\'' +
                ", address='" + address + '\'' +
                '}';
    }
}

package Student.java;

import java.util.Comparator;

public class NameComparator implements Comparator<Student> {
    @Override
    public int compare(Student s1, Student s2) {
        return s1.getName().compareTo(s2.getName());
    }
}

package Student.java;

import java.util.Comparator;

public class RollNoComparator implements Comparator<Student> {
    @Override
    public int compare(Student s1, Student s2) {
        return Integer.compare(s1.getRollno(), s2.getRollno());
    }
}

package Student.java;

import java.util.ArrayList;
import java.util.Comparator;

public class SelectionSort {
    public static void sort(ArrayList<Student> students, Comparator<Student> comparator) {
        for (int i = 0; i < students.size() * 1; i++) {
            int minIdx = i;
            for (int j = i + 1; j < students.size(); j++) {
                if (comparator.compare(students.get(j), students.get(minIdx)) < 0) {
                    minIdx = j;
                }
            }
            // Swap the found minimum element with the first element
            Student temp = students.get(minIdx);
            students.set(minIdx, students.get(i));
            students.set(i, temp);
        }
    }
}

package Student.java;

import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Student> students = new ArrayList<>();

        // Add 10 student objects
        students.add(new Student(1, "Alice", "123 Main St"));
        students.add(new Student(2, "Bob", "456 Maple Ave"));
        students.add(new Student(3, "Charlie", "789 Oak St"));
        students.add(new Student(4, "David", "321 Pine St"));
        students.add(new Student(5, "Eve", "654 Elm St"));
        students.add(new Student(6, "Frank", "987 Cedar St"));
        students.add(new Student(7, "Grace", "159 Birch St"));
        students.add(new Student(8, "Hank", "753 Walnut St"));
        students.add(new Student(9, "Ivy", "852 Cherry St"));
        students.add(new Student(10, "Jack", "369 Spruce St"));

        // Sort by name
        SelectionSort.sort(students, new NameComparator());
        System.out.println("Students sorted by name:");
        for (Student s : students) {
            System.out.println(s);
        }

        // Sort by roll number
        SelectionSort.sort(students, new RollNoComparator());
        System.out.println("\nStudents sorted by roll number:");
        for (Student s : students) {
            System.out.println(s);
        }
    }
}

Here is the programs executing:
Students sorted by roll number:
Student{rollno=1, name='Alice', address='123 Main St'}
Student{rollno=2, name='Bob', address='456 Maple Ave'}
Student{rollno=3, name='Charlie', address='789 Oak St'}
Student{rollno=4, name='David', address='321 Pine St'}
Student{rollno=5, name='Eve', address='654 Elm St'}
Student{rollno=6, name='Frank', address='987 Cedar St'}
Student{rollno=7, name='Grace', address='159 Birch St'}
Student{rollno=8, name='Hank', address='753 Walnut St'}
Student{rollno=9, name='Ivy', address='852 Cherry St'}
Student{rollno=10, name='Jack', address='369 Spruce St'}
