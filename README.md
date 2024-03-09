import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.File;
import java.io.IOException;

public class ExamSeatingSystem {
    private static JFrame frame;
    private static JPanel homePanel;
    private static JPanel roomManagementPanel;
    private static JPanel dataInputPanel;
    private static JPanel notificationPanel;
    private static JPanel uploadPanel;

    public static void main(String[] args) {
        frame = new JFrame("Exam Seating System");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(600, 400);
        frame.setLayout(new BorderLayout());

        homePanel = new JPanel(new BorderLayout());
        homePanel.setBackground(Color.WHITE);

        JLabel homeLabel = new JLabel("Home Page");
        homeLabel.setHorizontalAlignment(SwingConstants.CENTER);
        Font labelFont = homeLabel.getFont();
        homeLabel.setFont(new Font(labelFont.getName(), Font.PLAIN, 20));
        homePanel.add(homeLabel, BorderLayout.CENTER);

        JButton homeButton = new JButton("Home");
        homeButton.setEnabled(false);
        homeButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                frame.getContentPane().removeAll();
                frame.add(homePanel, BorderLayout.CENTER);
                frame.revalidate();
                frame.repaint();
            }
        });

        roomManagementPanel = new JPanel(new BorderLayout());
        roomManagementPanel.setBackground(Color.WHITE);

        JLabel roomManagementLabel = new JLabel("Room Management Page");
        roomManagementLabel.setHorizontalAlignment(SwingConstants.CENTER);
        roomManagementLabel.setFont(new Font(labelFont.getName(), Font.PLAIN, 20));
        roomManagementPanel.add(roomManagementLabel, BorderLayout.CENTER);

        JButton roomManagementButton = new JButton("Room Management");
        roomManagementButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                frame.getContentPane().removeAll();
                frame.add(roomManagementPanel, BorderLayout.CENTER);
                frame.revalidate();
                frame.repaint();
            }
        });

        dataInputPanel = new JPanel(new BorderLayout());
        dataInputPanel.setBackground(Color.WHITE);

        JLabel dataInputLabel = new JLabel("Data Input Page");
        dataInputLabel.setHorizontalAlignment(SwingConstants.CENTER);
        dataInputLabel.setFont(new Font(labelFont.getName(), Font.PLAIN, 20));
        dataInputPanel.add(dataInputLabel, BorderLayout.CENTER);

        JButton dataInputButton = new JButton("Data Input");
        dataInputButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                frame.getContentPane().removeAll();
                frame.add(dataInputPanel, BorderLayout.CENTER);
                frame.revalidate();
                frame.repaint();
            }
        });

        notificationPanel = new JPanel(new BorderLayout());
        notificationPanel.setBackground(Color.WHITE);

        JLabel notificationLabel = new JLabel("Notification Page");
        notificationLabel.setHorizontalAlignment(SwingConstants.CENTER);
        notificationLabel.setFont(new Font(labelFont.getName(), Font.PLAIN, 20));
        notificationPanel.add(notificationLabel, BorderLayout.CENTER);

        JButton notificationButton = new JButton("Notification");
        notificationButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                frame.getContentPane().removeAll();
                frame.add(notificationPanel, BorderLayout.CENTER);
                frame.revalidate();
                frame.repaint();
            }
        });

        uploadPanel = new JPanel(new BorderLayout());
        uploadPanel.setBackground(Color.WHITE);

        JLabel uploadLabel = new JLabel("Upload CSV File");
        uploadLabel.setHorizontalAlignment(SwingConstants.CENTER);
        uploadLabel.setFont(new Font(labelFont.getName(), Font.PLAIN, 20));
        uploadPanel.add(uploadLabel, BorderLayout.CENTER);

        JButton uploadButton = new JButton("Upload CSV File");
        uploadButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                JFileChooser fileChooser = new JFileChooser();
                int returnValue = fileChooser.showOpenDialog(null);
                if (returnValue == JFileChooser.APPROVE_OPTION) {
                    File selectedFile = fileChooser.getSelectedFile();
                    // Process the selected CSV file
                    try {
                        processCSVFile(selectedFile);
                    } catch (IOException ex) {
                        ex.printStackTrace();
                    }
                }
            }
        });

        JPanel buttonPanel = new JPanel(new FlowLayout(FlowLayout.CENTER));
        buttonPanel.add(homeButton);
        buttonPanel.add(roomManagementButton);
        buttonPanel.add(dataInputButton);
        buttonPanel.add(notificationButton);
        buttonPanel.add(uploadButton);
        frame.add(buttonPanel, BorderLayout.NORTH);

        frame.add(homePanel, BorderLayout.CENTER);

        frame.setVisible(true);
    }

    private static void processCSVFile(File file) throws IOException {
        // Process the CSV file
        // For demonstration, we simply print the file name
        System.out.println("Selected file: " + file.getName());
    }
}
