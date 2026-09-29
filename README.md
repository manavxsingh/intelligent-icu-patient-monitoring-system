import java.util.Random;

public class ICUPatientMonitoringSystem {

    // Threshold values for alerts
    private static final int MAX_HEART_RATE = 100;
    private static final int MIN_HEART_RATE = 60;
    private static final double MAX_TEMPERATURE = 38.0; // Celsius
    private static final double MIN_TEMPERATURE = 36.0; // Celsius
    private static final int MIN_OXYGEN_LEVEL = 90; // percentage

    public static void main(String[] args) {
        // Simulating patient vital data monitoring
        // In real-world, this data would come from sensors
        Random random = new Random();

        for (int i = 0; i < 10; i++) {  // simulate 10 readings
            int heartRate = 50 + random.nextInt(70);          // 50 to 120 bpm
            double temperature = 35.0 + random.nextDouble() * 5.0; // 35.0 to 40.0 Celsius
            int oxygenLevel = 85 + random.nextInt(20);        // 85% to 105%

            System.out.println("Reading " + (i + 1));
            System.out.println("Heart Rate: " + heartRate + " bpm");
            System.out.println("Temperature: " + String.format("%.1f", temperature) + " °C");
            System.out.println("Oxygen Level: " + oxygenLevel + " %");

            checkVitals(heartRate, temperature, oxygenLevel);

            System.out.println("--------------------");

            // Pause to mimic real-time gap (not necessary in real system)
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                break;
            }
        }
    }

    private static void checkVitals(int heartRate, double temperature, int oxygenLevel) {
        if (heartRate > MAX_HEART_RATE) {
            System.out.println("Alert: High heart rate! Immediate attention needed.");
        } else if (heartRate < MIN_HEART_RATE) {
            System.out.println("Alert: Low heart rate! Immediate attention needed.");
        }

        if (temperature > MAX_TEMPERATURE) {
            System.out.println("Alert: High temperature detected!");
        } else if (temperature < MIN_TEMPERATURE) {
            System.out.println("Alert: Low temperature detected!");
        }

        if (oxygenLevel < MIN_OXYGEN_LEVEL) {
            System.out.println("Alert: Low oxygen level detected!");
        }
    }
}
