---
title: Android Bluetooth tutorial
description: Write a program to turn on, get visible,list device's and turn off Bluetooth with the help of GUI
author: ranjit
date: 2024-04-03 08:17:00 +0800
categories: [Blogging, Demo]
tags: [typography]
pin: true
math: true
mermaid: true
---
<h2>activity_main.xml</h2>
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">


    <uses-permission android:name="android.permission.BLUETOOTH" />
    <uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.PracticalMad"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <meta-data
            android:name="preloaded_fonts"
            android:resource="@array/preloaded_fonts" />
    </application>

</manifest>
```
<h2>ActivityMain.java</h2>
```
package com.example.practicalmad;

import android.bluetooth.BluetoothAdapter;
import android.bluetooth.BluetoothDevice;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.Button;
import android.widget.ListView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;
import java.util.Set;

public class MainActivity extends AppCompatActivity {
    private BluetoothAdapter bluetoothAdapter;
    private Button turnOnBtn, turnOffBtn, visibleBtn, listDevicesBtn;
    private ListView devicesListView;
    private ArrayAdapter<String> devicesArrayAdapter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize BluetoothAdapter
        bluetoothAdapter = BluetoothAdapter.getDefaultAdapter();

        // UI components
        turnOnBtn = findViewById(R.id.turn_on_btn);
        turnOffBtn = findViewById(R.id.turn_off_btn);
        visibleBtn = findViewById(R.id.visible_btn);
        listDevicesBtn = findViewById(R.id.list_devices_btn);
        devicesListView = findViewById(R.id.devices_list_view);

        devicesArrayAdapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1);
        devicesListView.setAdapter(devicesArrayAdapter);

        // Button click listeners using lambda expressions
        turnOnBtn.setOnClickListener(v -> turnOnBluetooth());

        turnOffBtn.setOnClickListener(v -> turnOffBluetooth());

        visibleBtn.setOnClickListener(v -> makeDeviceVisible());

        listDevicesBtn.setOnClickListener(v -> listPairedDevices());
    }

    // Method to turn on Bluetooth
    private void turnOnBluetooth() {
        if (!bluetoothAdapter.isEnabled()) {
            Intent enableBluetoothIntent = new Intent(BluetoothAdapter.ACTION_REQUEST_ENABLE);
            startActivity(enableBluetoothIntent);
            Toast.makeText(getApplicationContext(), "Bluetooth turned on", Toast.LENGTH_SHORT).show();
        } else {
            Toast.makeText(getApplicationContext(), "Bluetooth is already on", Toast.LENGTH_SHORT).show();
        }
    }

    // Method to turn off Bluetooth
    private void turnOffBluetooth() {
        if (bluetoothAdapter.isEnabled()) {
            bluetoothAdapter.disable();
            Toast.makeText(getApplicationContext(), "Bluetooth turned off", Toast.LENGTH_SHORT).show();
        } else {
            Toast.makeText(getApplicationContext(), "Bluetooth is already off", Toast.LENGTH_SHORT).show();
        }
    }

    // Method to make device visible to other devices
    private void makeDeviceVisible() {
        Intent visibleIntent = new Intent(BluetoothAdapter.ACTION_REQUEST_DISCOVERABLE);
        startActivity(visibleIntent);
    }

    // Method to list paired devices
    private void listPairedDevices() {
        Set<BluetoothDevice> pairedDevices = bluetoothAdapter.getBondedDevices();
        devicesArrayAdapter.clear();

        if (pairedDevices.size() > 0) {
            for (BluetoothDevice device : pairedDevices) {
                devicesArrayAdapter.add(device.getName() + "\n" + device.getAddress());
            }
        } else {
            Toast.makeText(getApplicationContext(), "No paired devices found", Toast.LENGTH_SHORT).show();
        }
    }
}
```
<h2>Permisions </h2>
```

    <uses-permission android:name="android.permission.BLUETOOTH" />
    <uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```
