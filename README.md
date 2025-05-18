# Emergency Ambulance Dispatch Agent

This project simulates an emergency ambulance dispatch system using a conversational agent built with Python. The agent coordinates dispatch operations by confirming accidents, determining the user’s location (without outputting coordinates), and iterating through nearby hospitals until an ambulance is approved.

## Overview

- **Accident Confirmation:** The user is prompted to confirm an accident before any further action.
- **Location Retrieval:** The agent retrieves the user's location using a mock `GetCurrentLocationTool` (coordinates are used for processing but not output).
- **Ambulance Dispatch:** The agent uses a mock `ContactAmbulanceTool` to contact nearby hospitals (retrieved via `google_search`). 
  - If a hospital approves the dispatch (simulated with a 50% chance), the agent outputs the hospital name and estimated time of arrival.
  - If denied, the user is asked whether to contact the next hospital.
  - If no hospital approves, a fallback message with the contact number for West Visayas State University Medical Center is displayed.
- **Agent Chat:** The agent also acts as a conversational partner responding to additional ambulance requests.

## Prerequisites

- Python 3.12 (or later)
- [dotenv](https://pypi.org/project/python-dotenv/)
- Google ADK packages (e.g. `google.adk.agents` and `google.adk.tools`)
- A working `.env` file located in the project directory (e.g., `E:\googleCLI\emergency-ambulance\.env`) for environment variables

## Installation

1. Clone the repository or copy the project files into your working directory.
2. Create and configure your `.env` file with the necessary environment variables.
3. Install the required Python dependencies. For example:

   ```bash
   pip install python-dotenv
   pip install [other-required-packages]
   ```

## Project Structure

- **agent.py:**  
  Contains the main agent configuration and logic for handling ambulance dispatch operations. It confirms accidents, retrieves the user's location, queries nearby hospitals, and iterates through dispatch attempts until approved.
  
- **ambulance_tools.py:**  
  Implements the tools using a base framework (`BaseTool`) to mimic location retrieval (`GetCurrentLocationTool`) and simulate contacting ambulance services (`ContactAmbulanceTool`).

## Usage

To run the agent:

1. Open a terminal and navigate to the project directory (e.g., `e:\googleCLI\emergency-ambulance`).
2. Run the agent script:

   ```bash
   python agent.py
   ```

3. Follow the command-line prompts:
   - Confirm if an accident occurred.
   - The system will then silently retrieve your location.
   - It will query nearby hospitals and attempt to dispatch an ambulance.
   - If a dispatch is denied, you’ll be prompted to attempt contacting another hospital.
   - If no hospital approves the dispatch, a fallback message will be displayed with a contact number.

## Notes

- The project is a mock simulation. No real ambulance service is contacted.
- Ensure that the `google_search` tool returns a list of hospital names.
- The agent uses the model `"gemini-2.0-flash-exp"`. Adjust the model parameter if necessary based on available models.
- Any trace or 404 messages related to the web server endpoints are part of the tracing/debugging setup and can be addressed separately if needed.

## License

[Specify your license here, if applicable.]

## Contact

For more information or if you run into issues, please contact the project maintainer.
