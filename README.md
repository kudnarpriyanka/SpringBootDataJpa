# SpringBootDataJpa

@PutMapping("/update/{empId}")
    public ResponseEntity<Employee> update(@PathVariable int empId, @RequestBody Employee employee) {
        Employee employee1 = employeeServiceImpl.findById(empId).orElseThrow(() -> new RecordNotFoundException("Employee ID Does Not Exist"));

        employee1.setEmpEmailId(employee.getEmpEmailId());
        employee1.setEmpPassword(employee.getEmpPassword());
        employee1.setEmpDOB(employee.getEmpDOB());
        employee1.setEmpContactNumber(employee.getEmpContactNumber());
        employee1.setEmpSalary(employee.getEmpSalary());
        employee1.setEmpAddress(employee.getEmpAddress());
        employee1.setEmpName(employee.getEmpName());

        return ResponseEntity.ok(employeeServiceImpl.update(employee1));
    }
