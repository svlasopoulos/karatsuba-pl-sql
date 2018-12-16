CREATE OR REPLACE FUNCTION karatsuba (x IN NUMBER, y IN NUMBER)
RETURN NUMBER 
IS 
   deg NUMBER;
   x1  NUMBER;
   x2  NUMBER;
   y1  NUMBER;
   y2  NUMBER;
   z0  NUMBER;
   z1  NUMBER;
   z2  NUMBER;
   len_x INT; 
   len_y INT;
BEGIN
   IF (x < 10) or (y < 10) THEN
      RETURN x*y;
   END IF;  
  /* calculates the size of the numbers */
  len_x := LENGTH (x);
  len_y := LENGTH (y);
  /* split the digit sequences about the middle */
  x1  := TO_NUMBER (SUBSTR ( TO_CHAR(x), 1, CEIL (len_x/2)));
  x2  := TO_NUMBER (SUBSTR ( TO_CHAR(x), CEIL (len_x/2)+1));
  y1  := TO_NUMBER (SUBSTR ( TO_CHAR(y), 1, CEIL (len_y/2)));
  y2  := TO_NUMBER (SUBSTR ( TO_CHAR(y), CEIL (len_y/2)+1));
  --dbms_output.put_line(x1||','||x2||','||y1||','||y2);
  deg := FLOOR (len_x/2);
  /* 3 calls made to numbers approximately half the size */
  z0 := karatsuba (x1, y1);
  --dbms_output.put_line('z0='||z0);
  z2 := karatsuba (x2, y2);
  --dbms_output.put_line('z2='||z2);
  z1 := karatsuba (x1+x2, y1+y2);
  --dbms_output.put_line('z1='||z1);
  RETURN z0 * POWER(10, (2*deg))
         + z2
         + (z1 - z0 - z2) * POWER(10, deg);
END;
/
