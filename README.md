# Z_Transform
The goal is to find the sensor's transfer function having the input and output vectors.

First, I got the input and output (y and u) out of the sensor.m file, and split the **train and test** data as below:

```ruby
y_train = y(1:70);
y_test = y(71:100);
u_train = y(1:70);
u_test = y(71:100);
```

Then, finding n from the **inverse of z transform** as below:

```ruby
for j = 1:n-1
  phi_output(i-(n-1),j) = -y_train(i-j);
end
phi_input = zeros(70-n+1,3);
phi = [phi_output phi_input];
theta = inv(transpose(phi) * phi) * transpose(phi) * transpose_y;
y_Ls = phi * (theta)
j(1,n-3) = norm((y_train - y_Ls))^2;
```

I did the same for the **test** data (calculating j):

```ruby
j_test(1,n-3) = norm((y_test - y_Ls_test))^2;
```

By plotting the corresponding graphs:

![My Image](1.jpg)

As it can be seen, in n=15 the train and test data have the same results.


