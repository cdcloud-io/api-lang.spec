# api-lang.spec

## urls
- api-lang.org
- api-lang.dev
- api-lang.app

```
router "user_management" {
  base_path = "/users"

  resource "api_endpoint" "get_user" {
    method       = "GET"
    path         = "/{id}"
    description  = "Retrieve user details by ID"
    logging      = true
    auth         = true
    telemetry    = true

    response {
      status_code = 200
      body        = <<-EOF
      {
        "id": "string",
        "name": "string",
        "email": "string",
        "created_at": "string"
      }
      EOF
    }

    error_responses {
      status_code = 404
      body        = <<-EOF
      {
        "error": "User not found"
      }
      EOF
    }
  }

  resource "api_endpoint" "create_user" {
    method       = "POST"
    path         = ""
    description  = "Create a new user"
    logging      = true
    auth         = true
    telemetry    = false

    request {
      body = <<-EOF
      {
        "name": "string",
        "email": "string",
        "password": "string"
      }
      EOF
    }

    response {
      status_code = 201
      body        = <<-EOF
      {
        "id": "string",
        "name": "string",
        "email": "string",
        "created_at": "string"
      }
      EOF
    }

    error_responses {
      status_code = 400
      body        = <<-EOF
      {
        "error": "Invalid input data"
      }
      EOF
    }
  }
}
```
