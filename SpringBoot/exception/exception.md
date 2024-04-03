## ResponseEntityExceptionHandler
### enum exception 처리
```
@RestControllerAdvice
public class ControllerErrorHandler extends ResponseEntityExceptionHandler {
    public static final String BAD_REQUEST = "BAD_REQUEST";
    @Override
    public ResponseEntity<Object> handleHttpMessageNotReadable(HttpMessageNotReadableException exception,
                                                               HttpHeaders headers, HttpStatus status, WebRequest request) {
        String genericMessage = "Unacceptable JSON " + exception.getMessage();
        String errorDetails = genericMessage;

        if (exception.getCause() instanceof InvalidFormatException) {
            InvalidFormatException ifx = (InvalidFormatException) exception.getCause();
            if (ifx.getTargetType()!=null && ifx.getTargetType().isEnum()) {
                errorDetails = String.format("Invalid enum value: '%s' for the field: '%s'. The value must be one of: %s.",
                        ifx.getValue(), ifx.getPath().get(ifx.getPath().size()-1).getFieldName(), Arrays.toString(ifx.getTargetType().getEnumConstants()));
            }
        }
        ErrorResponse errorResponse = new ErrorResponse();
        errorResponse.setTitle(BAD_REQUEST);
        errorResponse.setDetail(errorDetails);
        return handleExceptionInternal(exception, errorResponse, headers, HttpStatus.BAD_REQUEST, request);
    }

}
```