public Segment getSegment(){

        int bufferSize = 0;
        float timeout = 0;s
        if ( this.port.getType().equals("RS232")){
                bufferSize = RS232.DEFAULT_SIZE;
                timeout = RS232.DEFAULT_TIMEOUT;
        }
        if ( this.port.getType().equals("USB")){
                bufferSize = USB.DEFAULT_SIZE;
                timeout = USB.DEFAULT_TIMEOUT;
        }
        
        byte[] buffer = new byte[ bufferSize ];
        
        boolean status = this.port.readBytes(buffer , timeout);
        if(status){
                return this.parser.parse( buffer );
        } else {
                return null;
        }
        
}
                
