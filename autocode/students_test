package coverage

import (
	"os"
	"fmt"
	"time"
	"testing"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

func genTestDate(aIndex int) time.Time {
	return time.Date(2022, 1, 1, 0, 0, 0, 0, time.UTC).AddDate(0, 0, aIndex)
}

func newTestPerson(aIndex int) Person {
	return Person{
		firstName: fmt.Sprintf("fn%v", aIndex),
		lastName: fmt.Sprintf("ln%v", aIndex),
		birthDay: genTestDate(aIndex),
	}
}

func Test_People_Len(t *testing.T) {
	lTestPeopleEmpty := People{}
	lTestPeople2 := People{newTestPerson(1), newTestPerson(2)}

	if lTestPeopleEmpty.Len() != 0 {
		t.Error("zero length error")
	}
	
	if lTestPeople2.Len() != 2{
		t.Error("2 length error")
	}
}

func Test_People_Less(t *testing.T) {
	lTestPeople := People{
		Person{firstName: "Ivan", lastName: "Petrov", birthDay: time.Date(2020, 1, 1, 0, 0, 0, 0, time.UTC)},
		Person{firstName: "Ivan", lastName: "Petrov", birthDay: time.Date(2021, 1, 1, 0, 0, 0, 0, time.UTC)},
		Person{firstName: "Alex", lastName: "Petrov", birthDay: time.Date(2020, 1, 1, 0, 0, 0, 0, time.UTC)},
	}

	if lTestPeople.Less(0, 1) || lTestPeople.Less(0, 2){
		t.Error("Less failed")
	}
}

func Test_People_Swap(t *testing.T) {
	lTestPeople := People{newTestPerson(1), newTestPerson(2)}

	lTestPeople.Swap(0, 1)

	if lTestPeople[0].firstName != "fn2"{
		t.Error("Swap failed ")
	}
}

func Test_Matrix_New(t *testing.T) {
	var lMatrix *Matrix
	var err error

	_, err = New("1 2\n3")
	if err.Error() != "Rows need to be the same length" {
		t.Error("Same length failed")
	}

	_, err = New("1 2\na b")
	if err == nil {
		t.Error("New Matrix failed (Atoi)")
	}

	lMatrix, err = New("1 2\n3 4")
	if err != nil {
		t.Error("New Matrix failed")
	}

	if lMatrix.Set(0, 4, 4){
		t.Error("Matrix Set(4, 4, 4) failed")
	}

	if !lMatrix.Set(0, 0, 5){
		t.Error("Matrix Set(0, 0, 5) failed")
	}

	lMatrix.Cols()
	lMatrix.Rows()

}
