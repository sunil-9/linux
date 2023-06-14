## Services

To add a service in Linux, you typically need to create a systemd service unit file. Here's a step-by-step guide on how to add a service in Linux (assuming you are using a systemd-based distribution like Ubuntu):

1. Create a service unit file:
   ```
   sudo nano /etc/systemd/system/my-service.service
   ```

   Replace `my-service` with a meaningful name for your service.

2. In the nano editor, enter the following content for the service unit file:
   ```
   [Unit]
   Description=My Service
   After=network.target
   
   [Service]
   ExecStart=/path/to/your/service-executable
   WorkingDirectory=/path/to/your/service-working-directory
   Restart=always
   
   [Install]
   WantedBy=multi-user.target
   ```

   Make sure to replace `/path/to/your/service-executable` with the actual path to your service executable and `/path/to/your/service-working-directory` with the directory where your service should run.

   You can customize other options in the service unit file according to your specific requirements.

3. Save the file by pressing `Ctrl+O`, and then exit nano by pressing `Ctrl+X`.

4. Reload systemd to load the new service(if your are creating service for the first time then you dont need this step):
   ```
   sudo systemctl daemon-reload
   ```

5. Start the service:
   ```
   sudo systemctl start my-service
   ```

   Replace `my-service` with the name you used for your service in the unit file.

6. Verify the status of the service:
   ```
   sudo systemctl status my-service
   ```

   This command will display the current status and some information about the service.

7. Enable the service to start automatically at boot:
   ```
   sudo systemctl enable my-service
   ```

   This ensures that your service will be started automatically when the system boots up.

That's it! Your service should now be added and running on your Linux server. You can use `systemctl` commands (e.g., `start`, `stop`, `restart`, `status`) to manage the service as needed.

## check available service

To check the list of services running on a Linux server, you can use the `systemctl` command in linux. Here's how you can do it:

1. Open a terminal on your Ubuntu server.
2. Type the following command and press Enter:
   ```
   systemctl list-units --type=service
   ```

This command will display a list of all services along with their current status (whether they are running or not) on your Ubuntu server.

If you want to view more details about each service, you can add the `--all` flag to the command:
```
systemctl list-units --type=service --all
```

This will provide additional information such as the service description, whether the service is enabled to start at boot, and its current state.

Note that you may need administrative privileges (sudo) to execute this command, depending on your system configuration.
