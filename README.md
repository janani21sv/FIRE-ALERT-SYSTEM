# FIRE-ALERT-SYSTEM
KEY WORDS: Fire alarm system, Tiva C microcontroller, Flame sensor, ESP32 module, GPS module, Buzzer, Sensor data processing, Wi-Fi connectivity, Email notification, False alarm reduction, Sensor integration.

OVERVIEW:
This project outlines the development of a smart fire alarm system leveraging the Tiva C microcontroller, a flame sensor, a buzzer, the ESP32 module, and a GPS module. The system is designed to detect fire through connected sensor, introduced a five-second delay to avoid false alarms, and subsequently trigger a buzzer for local alerts while also sending an email notification for remote alerts. Additionally, the GPS module is integrated to determine the longitude and latitude of the current location, which is included in the email notification. The Tiva C processes sensor data, manages the delay, and communicates with the ESP32, which handles Wi-Fi connectivity, email dispatch, and retrieves location data from the GPS module. This comprehensive system enhances fire safety by providing immediate on-site alerts and detailed remote notifications, ensuring rapid response and protection for both residential and commercial environments. Key features include reliable communication between components, and a mechanism to reduce false alarms. 

METHODOLOGY:
Circuit Setup:
The Tiva C microcontroller is interfaced with a flame sensor, buzzer, GPS module, and ESP32. All components are connected according to designated pin configurations, with proper power (3.3V) and ground lines to ensure stability. The setup was validated using circuit and block diagrams to ensure reliability before implementation.

Flame Sensor & Fire Detection:
The flame sensor’s analog output is connected to Tiva C's PB\_5 pin. Using 'analogRead()', the system continuously monitors fire levels. A threshold value is set to identify the presence of a flame, and a timer tracks the event. If the flame persists for over 5 seconds, it is confirmed as a fire incident.

Buzzer Activation:
When fire detection exceeds 5 seconds, the buzzer connected to pin PA\_2 is triggered using 'digitalWrite()'. This produces a loud continuous sound alerting nearby individuals. The buzzer stays active until the system is reset or the fire is extinguished.

ESP32 Communication:
A digital pin (PE\_0) on the Tiva C board sends a trigger signal to the ESP32 module via serial communication. Upon receiving the signal, the ESP32 initiates email alerts and can activate other safety measures. This enables remote monitoring and action even if no one is physically present.

GPS Tracking:
The GPS module is connected to the ESP32's RX2 pin. Using 'HardwareSerial', GPS data is captured and parsed with the TinyGPS++ library. Latitude and longitude values are extracted and updated every second using 'smartDelay()'. These coordinates are included in alert emails for precise location sharing.

Email Notification Setup:
ESP32 connects to Wi-Fi and uses the 'ESP_Mail_Client' library to send email alerts. The email includes a Google Maps link with the device's location. SMTP settings (host, port, and credentials) are predefined, and the 'sendEmail()' function is triggered when fire is detected. The 'smtpCallback()' function handles delivery status feedback, ensuring reliable communication.

BLOCK DIAGRAM:

<img width="472" height="343" alt="image" src="https://github.com/user-attachments/assets/2b5b46b7-6a5d-48ac-9e98-adefe615b580" />
<img width="472" height="343" alt="image" src="https://github.com/user-attachments/assets/a8915940-6b31-442e-a093-bd81312598b5" />

SAMPLE OUTPUT SCREENSHOTS:

<img width="472" height="343" alt="image" src="https://github.com/user-attachments/assets/34b8d384-033b-4fea-a854-1f7fef2a27e8" />
<img width="472" height="343" alt="image" src="https://github.com/user-attachments/assets/a537579d-3abe-4b0d-8e24-6175c2448997" />
<img width="472" height="343" alt="image" src="https://github.com/user-attachments/assets/0eaa23ab-e0e5-4058-b944-bc615f2603f5" />
<img width="472" height="343" alt="image" src="https://github.com/user-attachments/assets/f03d8faf-44ac-42e1-94ea-d5b9a1df3fe8" />
<img width="472" height="343" alt="image" src="https://github.com/user-attachments/assets/a4b761d6-eb8e-45dd-b83f-b3df6bfec274" />


CONCLUSION:
This smart fire alarm system effectively combines the Tiva C microcontroller, ESP32 module, GPS, and buzzer to detect and respond to fire incidents in real-time. It provides both local alerts and remote email notifications with precise GPS location, ensuring quick and informed emergency responses. The five-second detection delay helps reduce false alarms, improving system reliability. Overall, the project demonstrates how embedded systems and IoT technologies can enhance fire safety for homes, offices, and industrial settings.
