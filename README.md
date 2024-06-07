# Contact Form API with Spam Detection

This is an open-source API for submitting contact forms from a web page. It uses ChatGPT's API to detect and prevent spam submissions.

## Features

- Submit contact form data
- Evaluate submissions for spam using ChatGPT
- Allow legitimate submissions and reject spam

## Prerequisites

- Node.js
- npm or yarn
- OpenAI API key

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/contact-form-api.git
    cd contact-form-api
    ```

2. Install the dependencies:
    ```bash
    npm install
    ```
    or
    ```bash
    yarn install
    ```

3. Create a `.env` file in the project root and add the following environment variables:
    ```
    PORT=5000
    OPENAI_API_KEY=your_openai_api_key
    ALLOWED_ORIGINS=http://localhost:3000,http://example.com
    ```

## Usage

1. Start the server:
    ```bash
    npm start
    ```
    or
    ```bash
    yarn start
    ```

2. Send a POST request to `/api/contact` with the following JSON body:
    ```json
    {
      "name": "John Doe",
      "email": "john.doe@example.com",
      "subject": "Inquiry",
      "message": "I would like to know more about your services."
    }
    ```

3. The server will evaluate the submission for spam and respond accordingly:
    - If the submission is legitimate, it will respond with a success message.
    - If the submission is identified as spam, it will respond with an error message.

## API Endpoints

### POST `/api/contact`

- **Request Body**:
    ```json
    {
      "name": "string",
      "email": "string",
      "subject": "string",
      "message": "string"
    }
    ```

- **Response**:
    - Success: `200 OK`
        ```json
        {
          "message": "Form submitted successfully"
        }
        ```
    - Error: `400 Bad Request`
        ```json
        {
          "error": "Your message was identified as spam or risky content."
        }
        ```
    - Error: `500 Internal Server Error`
        ```json
        {
          "error": "Internal server error"
        }
        ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
