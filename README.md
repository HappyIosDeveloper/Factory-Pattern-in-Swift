# Factory Pattern in Swift
Simple example of Factory Pattern written in Swift

# You can save the below code in Playground or download the depo file.

    import UIKit
    
    struct Car {
    
        enum CarType { case sedan, hatchBack, suv, van, coupe }
        enum CarColor { case black, white, red, blue }
    
        var type: CarType
        var color: CarColor
    
        func printDetail() {
            print("car type: \(type), color: \(color)")
        }
    }
    
    class CarFactory {
    
        enum Gender: CaseIterable { case boy, girl, man, woman }
        var gender: Gender = .man
    
        static func makeCar(for gender: Gender)-> Car {
            switch gender {
            case .boy:
                return Car(type: .coupe, color: .black)
            case .girl:
                return Car(type: .hatchBack, color: .red)
            case .man:
                return Car(type: .sedan, color: .white)
            case .woman:
                return Car(type: .suv, color: .blue)
            }
        }
    }
    
    let genders = CarFactory.Gender.allCases
    for gender in genders {
        CarFactory.makeCar(for: gender).printDetail()
    }
    
    /*
    Here is the output:
    
    car type: coupe, color: black
    car type: hatchBack, color: red
    car type: sedan, color: white
    car type: suv, color: blue
    */
    
