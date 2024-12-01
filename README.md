# Washing-Machine
`timescale 10ns / 1ps
module new_test();
	reg clk, reset, door_close, start, filled, detergent_added, cycle_timeout, drained, spin_timeout;
	wire door_lock, motor_on, fill_value_on, drain_value_on, done, soap_wash, water_wash; 
	
	
automatic_washing_machine machine1(clk, reset, door_close, start, filled, detergent_added, cycle_timeout, drained, spin_timeout, door_lock, motor_on, fill_value_on, drain_value_on, done, soap_wash, water_wash);
    reg clk, reset, door_close, start, filled, detergent_added, cycle_timeout, drained, spin_timeout;
    wire door_lock, motor_on, fill_value_on, drain_value_on, done, soap_wash, water_wash;

    // Instantiate the automatic washing machine module
    automatic_washing_machine machine1 (
        .clk(clk),
        .reset(reset),
        .door_close(door_close),
        .start(start),
        .filled(filled),
        .detergent_added(detergent_added),
        .cycle_timeout(cycle_timeout),
        .drained(drained),
        .spin_timeout(spin_timeout),
        .door_lock(door_lock),
        .motor_on(motor_on),
        .fill_value_on(fill_value_on),
        .drain_value_on(drain_value_on),
        .done(done),
        .soap_wash(soap_wash),
        .water_wash(water_wash)
    );
    // Initialize the waveform dump
    initial begin
        $dumpfile("dump.vcd");
        $dumpvars(0, new_test);
    end
    // Clock generation
    always begin
        #5 clk = ~clk; // Toggle clock every 5 time units
    end
    // Test sequence
    initial begin
        // Initialize inputs
        clk = 0;
        reset = 1;
        start = 0;
        door_close = 0;
        filled = 0;
        drained = 0;
        detergent_added = 0;
        cycle_timeout = 0;
        spin_timeout = 0;
        // Apply test vectors
        #5 reset = 0;
        #5 start = 1; door_close = 1;
        #10 filled = 1;
        #10 detergent_added = 1;
        #10 cycle_timeout = 1;
        #10 drained = 1;
        #10 spin_timeout = 1;
        #10 $finish; // End the simulation
    end
    // Monitor signals
    initial begin
        $monitor("Time=%d, Clock=%b, Reset=%b, Start=%b, Door_Close=%b, Filled=%b, Detergent_Added=%b, Cycle_Timeout=%b, Drained=%b, Spin_Timeout=%b, Door_Lock=%b, Motor_On=%b, Fill_Valve_On=%b, Drain_Valve_On=%b, Soap_Wash=%b, Water_Wash=%b, Done=%b",
                 $time, clk, reset, start, door_close, filled, detergent_added, cycle_timeout, drained, spin_timeout, door_lock, motor_on, fill_value_on, drain_value_on, soap_wash, water_wash, done);
    end

	
	
	initial
		
	begin
	clk = 0;
		reset = 1;
		start = 0;
		door_close = 0;
		filled = 0;
		drained = 0;
		detergent_added = 0;
		cycle_timeout = 0;
		spin_timeout = 0;
		
		#5 reset=0;
		#5 start=1;door_close=1;
		#10 filled=1;
		#10 detergent_added=1;
		//filled=0;
		#10 cycle_timeout=1;
		//detergent_added=0;
		#10 drained=1;
		//cycle_timeout=0;
		#10 spin_timeout=1;
		//drained=0;
		
		/*
		
		#0 reset = 0;
		#2 start = 1;
		#4 door_close = 1;
		#3 filled = 1;
		#3 detergent_added = 1;
		#2 cycle_timeout = 1;
		#2 drained = 1; 
		#3 spin_timeout = 1;
		*/
	end
	
	always
	begin
		#5 clk = ~clk;
	end
	
	initial
	begin
		$monitor("Time=%d, Clock=%b, Reset=%b, start=%b, door_close=%b, filled=%b, detergent_added=%b, cycle_timeout=%b, drained=%b, spin_timeout=%b, door_lock=%b, motor_on=%b, fill_valve_on=%b, drain_valve_on=%b, soap_wash=%b, water_wash=%b, done=%b",$time, clk, reset, start, door_close, filled, detergent_added, cycle_timeout, drained, spin_timeout, door_lock, motor_on, fill_value_on, drain_value_on, soap_wash, water_wash, done);
	end
endmodule
