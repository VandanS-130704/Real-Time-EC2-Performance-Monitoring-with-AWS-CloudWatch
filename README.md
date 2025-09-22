# Real-Time EC2 Performance Monitoring with AWS CloudWatch

This project demonstrates how to configure AWS CloudWatch to monitor key performance metrics for an Amazon EC2 instance, specifically CPU utilization. It includes setting up a CloudWatch Alarm that automatically triggers when usage exceeds a predefined threshold, enabling proactive issue detection and performance analysis.

---

## 🚀 Overview

In any cloud environment, maintaining optimal performance and availability of compute resources is crucial. This project implements a robust monitoring system for an EC2 instance using native AWS services to provide real-time visibility into its operational health.

### Objectives:
* **Collect & Track Metrics:** Automatically collect the `CPUUtilization` metric from a specific EC2 instance.
* **Proactive Alerting:** Implement a CloudWatch Alarm to visually flag when the CPU metric crosses a defined threshold.
* **Performance Visibility:** Use CloudWatch dashboards and alarms to quickly identify and analyze performance bottlenecks.

---

## 🛠️ Services Used

* **Amazon EC2:** The virtual server (instance ID: `i-08cc5d5881f30226f`) whose performance is being monitored.
* **AWS CloudWatch:** The core service used for collecting metrics and setting up alarms.

---

## ⚙️ Implementation & Configuration

The core of this project is a CloudWatch Alarm configured to watch the EC2 instance's CPU. The alarm was set up with the following parameters to ensure it would trigger under specific load conditions.

### Alarm Configuration Details:
* **Metric:** `CPUUtilization`
* **Statistic:** `Average`
* **Period:** `1 minute`
* **Threshold:** Trigger when `CPUUtilization` is `>= 15%`
* **Evaluation Period:** `1` consecutive period (i.e., for 1 minute)
* **Actions:** No actions configured.

![Alarm Configuration Details](The%20Details%20pane%20showing%20the%20alarm%20state%20and%20configuration.jpg)

---

## 📊 Results and Verification

To test the setup, a load was generated on the EC2 instance to intentionally spike the CPU usage. The monitoring system performed exactly as expected.

### 1. Initial State: OK

Before the test, the EC2 instance's CPU utilization was low and stable. The CloudWatch alarm was in the **`OK`** state, indicating that performance was within the normal, defined limits.

![Initial Alarm State](The%20list%20of%20alarms%20showing%20the%20initial%20OK%20state.jpg)

### 2. CPU Spike Detected

The CloudWatch metric graph clearly shows the instance's CPU utilization was very low (under 5%) and then suddenly spiked to over 60% around **13:10**. This spike decisively crossed the 15% threshold (the red line).

![CPU Utilization Spike](Graph%20showing%20the%20CPU%20spike.jpg)

### 3. Alarm State Change: In Alarm

Once the CPU utilization crossed the 15% threshold and remained there for one minute, the alarm state immediately changed from `OK` to **`In alarm`** at **13:13:27 (Local Time)**. This change provides a clear visual indicator in the AWS console that a performance threshold has been breached.

![Alarm Triggered State](Dashboard%20showing%20the%20In-alarm%20status.jpg)

---

## ✅ Conclusion

This project successfully demonstrates a simple yet powerful server monitoring mechanism using AWS CloudWatch. By setting up metric-based alarms, DevOps teams gain immediate visibility into the health of their infrastructure. This automated monitoring is fundamental for maintaining system stability, ensuring high availability, and enabling teams to proactively investigate and resolve performance issues before they impact users.
