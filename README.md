SSH Proxy

The SSH Proxy is a lightweight, composable tool designed to handle SSH connections and delegate authentication and session management to an external application (RemoteApp). This project embodies the philosophy of simplicity, composability, and trust in external systems, making it an ideal building block for modern distributed systems.

Features
	•	Minimal Complexity: Focuses on core functionality, delegating other concerns to trusted external components.
	•	Flexibility: Configurable via environment variables and command-line arguments for seamless integration with development and production workflows.
	•	Error Handling: Graceful handling of errors and invalid inputs to ensure robust and predictable behavior.
	•	Extensibility: Built with abstractions like RemoteApp to enable future extension and customization.

How It Works
	1.	The SSH Proxy accepts incoming SSH connections.
	2.	It extracts the username and password from the session.
	3.	Credentials are forwarded to the RemoteApp for authentication and processing.
	4.	Results or errors from the RemoteApp are returned to the SSH client.

The proxy assumes a trusted network environment and delegates operational concerns (e.g., rate limiting, centralized logging) to the orchestration layer.

Getting Started

Requirements
	•	Python 3.8 or higher
	•	asyncssh library (pip install asyncssh)
	•	A compatible implementation of RemoteApp

Installation
	1.	Clone the repository:

git clone https://github.com/yourusername/ssh-proxy.git
cd ssh-proxy


	2.	Install dependencies:

pip install -r requirements.txt

Usage

The SSH Proxy can be configured via command-line arguments or environment variables. Command-line arguments take precedence over environment variables.

Command-Line Arguments
	•	--host: Host to bind the SSH server (default: 0.0.0.0)
	•	--port: Port to bind the SSH server (default: 8022)
	•	--key-path: Path to the SSH host key (default: ssh_host_key)
	•	--max-connections: Maximum concurrent connections (default: 100)

Example:

python ssh_proxy.py --host 127.0.0.1 --port 2222 --key-path ./ssh_host_key

Environment Variables
	•	SSH_HOST: Host to bind the SSH server
	•	SSH_PORT: Port to bind the SSH server
	•	SSH_KEY_PATH: Path to the SSH host key
	•	MAX_CONNECTIONS: Maximum concurrent connections

Example:

export SSH_HOST=127.0.0.1
export SSH_PORT=2222
export SSH_KEY_PATH=./ssh_host_key
python ssh_proxy.py

Default Configuration

If no command-line arguments or environment variables are provided, the proxy uses the following defaults:
	•	Host: 0.0.0.0
	•	Port: 8022
	•	Key Path: ssh_host_key
	•	Max Connections: 100

Development Philosophy

This project was developed using the principle of minimal complexity:
	•	Start with a simple prototype solving the core problem.
	•	Incrementally add only essential features to improve robustness.
	•	Delegate non-core responsibilities (e.g., authentication, logging, rate limiting) to trusted external systems.

This approach ensures the system remains composable, predictable, and easy to maintain.

License

This project is licensed under the MIT License. See the LICENSE file for details.

Contributing

Contributions are welcome! Please ensure that your changes align with the project’s philosophy of minimal complexity and composability.

To contribute:
	1.	Fork the repository.
	2.	Create a new branch for your feature or bug fix.
	3.	Submit a pull request with a clear description of your changes.

Acknowledgments

This project is inspired by the principles of building small, trusted, composable units. Special thanks to contributors and users who help refine and improve this tool.
