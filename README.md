# Washing-Machine
`timescale 10ns / 1ps
module new_test();
	reg clk, reset, door_close, start, filled, detergent_added, cycle_timeout, drained, spin_timeout;
	wire door_lock, motor_on, fill_value_on, drain_value_on, done, soap_wash, water_wash; 
	
	
automatic_washing_machine machine1(clk, reset, door_close, start, filled, detergent_added, cycle_timeout, drained, spin_timeout, door_lock, motor_on, fill_value_on, drain_value_on, done, soap_wash, water_wash);
    reg clk, reset, door_close, start, filled, detergent_added, cycle_timeout, drained, spin_timeout;
    wire door_lock, motor_on, fill_value_on, drain_value_on, done, soap_wash, water_wash;

   
