## ResponseEntityExceptionHandler
### enum exception 처리
```
@RestControllerAdvice
public class ControllerErrorHandler extends ResponseEntityExceptionHandler {

    public static final String BAD_REQUEST = "BAD_REQUEST";

    @Override
    public ResponseEntity<Object> handleHttpMessageNotReadable(HttpMessageNotReadableException exception,
                                                               HttpHeaders headers, HttpStatus status, WebRequest request) {

        String genericMessage = "Unacceptable JSON " + ex.getMessage();
        String errorDetails = genericMessage;

        if (ex.getCause() instanceof InvalidFormatException) {
            InvalidFormatException invalidFormatException = (InvalidFormatException) ex.getCause();
            if (invalidFormatException.getTargetType()!=null && invalidFormatException.getTargetType().isEnum()) {
                errorDetails = String.format("Invalid enum value: '%s' for the field: '%s'. The value must be one of: %s.",
                        invalidFormatException.getValue(),
                        invalidFormatException.getPath().get(invalidFormatException.getPath().size()-1).getFieldName(),
                        Arrays.toString(invalidFormatException.getTargetType().getEnumConstants()));
            }
        }

        ApiResponse<String> response = new ApiResponse<>(status, "error", errorDetails);

        return new ResponseEntity<>(response, status);

    }

}
```