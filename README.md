# StreamApi
Repo to study StreamApi Java 8

public class StreamsMain {

	public static void main(String[] args) {
		//All the next code are examples of the use of streams and lambdas
		
		//example 1 (print every element on arrayInt and count the amount of elements < 5)
		Integer[] arrayInt = {1,2,3,4,5,6,7};
		
		//convert the array into list
		List<Integer> list = Arrays.asList(arrayInt);
		// using streams
			//peek used to catch every value
			//mapToInt to convert every value on int
		int count = list.stream().peek(c -> {
			
			System.out.println("-"+ c);
			
		}).mapToInt(c -> c < 5 ? 1 : 0).sum();		
		System.out.println("Total of values < 5: "+ count);
		
		//example 2(comparing strings)
		
		String[] arrayString = {"Hola mundo","Hola españa","la vida es asi","Nuunca digas nunca"};
		List<String> listaString = Arrays.asList(arrayString);
		
		//1 solution using reduce
		String mayor = listaString.stream().reduce((a,b) -> {
			if (a.length() > b.length())
				return a;
			return b;
		}).get();
		System.out.println(mayor);
		
		//2 solution using max
		String mayor2 = listaString.stream().max(Comparator.comparing(String::length)).get();
		System.out.println(mayor2);
	}

}
